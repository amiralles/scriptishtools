## Gitmine
Let's suppose you have a to attack a large code base that you never 've seen
before. Where would you start from? How would you be productive from day one?

A common approach is try to find system's entry points and figure out some
execution paths from there. While that's fine (and usually works), 
some time is easy to search thru the code's history and look for pain points.

When I say "pain points" I mean code that changes often and also tends to 
change a lot. In general, this means that either, there is a whole lot 
going on in there, or is a really fragile part of the system, 
or what ever. *It's something that worth to take a look at*.

By using **gitmine** you will be able to tell which files changes 
often, who 've been working on those files, detect potencial refactors, 
and much more...

## How to install
TODO: 

## Commands
### Commits per file
This command will show you a list of file names and the commits count for each
file. This list is sort in descending order by commits count which means that 
you get to see first the files that change more often. (And probably, 
the most important ones).

```
gitmine cmpf
```

### Commits per file per author
This command is useful when you wanna see who had worked on 
what. As well as **cmpf** you will see a list of file names and commits count 
but this time it'll be **filter by author**.

```
gitmine cmpf amiralles
```
### What've been doing?
This command allows you to see what an author have been doing since a
given date.

```
# arguments:
# 'yyyy-MM-dd'
# author

gitmine wbd '2016-05-14' amiralles

```

### Ref Count
This command indexes all classes on a given srouce tree and creates a list
of references to those classes by looking at every file in the codebase.

While is not 100% accurate, it will give you an
idea of how many dependencies meybe affected by changes on a particular file.

```
# It 'll look for references to any class in the entire code base.
gitmine refcount '*.cs'

# It'll look for references to any class defined in foo.cs
gitmine refcount 'foo.cs'
```

### Leader Board
The *highscore* command allows you to see how many times a person committed to a given file. I
also see this command as a way to know who is the actual owner of the file, not the
guy who created it, but the one that works with it most of the time.

If you omit the filename, **gitmine** will show some sort of leader board based on
commits count.

```
# Will show commits count per author to a particular file.
gitmine hi foo.cs
```

```
# Will show a leader board based on commits count.
gitmine score
```




