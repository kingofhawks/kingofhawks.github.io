Intellij IDEA is a great IDE for Java development.

But sometimes IDEA14.1.4 will show many error messages for OSGi modules as this:

> The package xxx is not imported in the manifest

You could resolve that by doing this:

> File -> Settings -> Inspections -> OSGi -> Package accessibility, change the defulat sevirity "error" to "warning" or "info"