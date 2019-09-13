---
title: "Manipulate Paths and Filenames"
---
BASH scripts often require manipulation of the pathname of files/directories.

## Get Any Path in a Filename
You may need access to the target file's parent directory, or you may need the file/directory name seperated from it's path.

{% highlight bash startinline %}
# Example pathname
pathname=parent/child/target

echo $(basename $pathname)
# returns target

echo $(basename $(dirname $pathname))
# returns child

echo $(basename $(dirname $(dirname $pathname)))
#returns parent

{% endhighlight %}

## Strip Trailing Slash

{% highlight bash startinline %}
DIR=test/
SOURCE_DIR=${DIR%/}
echo $SOURCE_DIR
# returns test
{% endhighlight %}
