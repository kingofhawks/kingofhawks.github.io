[Pandas](http://pandas.pydata.org/) is the most popular data analysis tool for Python, which is based on Numpy.

The basic concept of pandas are Series and DateFrame.

Series are an array of data, associated with array of data labels:

> obj = Series([1,3,5,100],index=['a','b,'c',d'])

> obj.values

> obj['a']

> 'b' in obj  #like ordered dict

Also you could pass dict to Series:

> person = {'name': 'simon','age':30}

> obj2 = Series(person)

DataFrame represents a tabular data, it has both *row* and *column* index, it can be thought as a dict of Series.

It internally stores data as a two-dimension format.

The most common usage about DataFrame is from a dict of lists with equal length or Numpy arrys:

> data = {'name':['simon','grace'],'age':[36,33]}

> df = DataFrame(data)

> or df = DataFrame(data, columns=['name','age'])

> or df = DataFrame(data, columns=['name','age'],index=['one','two'])

> df.columns

You can access column of data with dict style or by attribute:

> df['name']

> df.age


Row can be accessed like:

> df.ix('one') #by indexing field

> df.values


### Reference

* Python for Data Analysis