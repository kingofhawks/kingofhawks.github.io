MongoDB's GridFS is a specification for storing and retrieving files that exceed the BSON-document size limit of 16MB.

You could use Pymongo to easily store files to MongoDB GridFS like this:

<code><pre>
import gridfs
fs = gridfs.GridFS(settings.DB)
file_id = fs.put(f)
print 'save file to GridFS:{}'.format(file_id)
</pre></code>


By default, GridFS uses two collections to store files with names prefixed by fs bucket:

* fs.files: *files* stores the file’s metadata.
* fs.chunks: *chunks* stores the binary chunks.

You can choose a different bucket name than fs, and create multiple buckets in a single database.

### References:
* [GridFS](http://docs.mongodb.org/manual/core/gridfs/)
* [When to Use GridFS](http://docs.mongodb.org/manual/faq/developers/#faq-developers-when-to-use-gridfs)