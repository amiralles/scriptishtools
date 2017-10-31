## Gitmine
Let's suppose you have to start working on a huge project, a really 
large code base that you never 've seen before. 
It would be possible for you to be productive from day one?

The answer, as almost everything else in tech, is "it depends!" ;) but where would you start? 

I don't know about you, but what I would normally do is to try to find 
entry points to the system or the API that I'll be working on, and try to find
from there some execution paths that allows me to understand what the system actually 
does. If the system has a tests project, I'd check that, too. 

While this approach is fine (and sometimes, it works too), can you be sure that you are 
looking at meaningfull execution paths, the most important ones? or the rigth set of tests? 
can you spot by just looking at the code where the bread and butter 
of the system really is?

If you are not familiar with the code base, chances are that you connot tell for sure if you are
looking at the right parts of the system. In this kind of situations is where you can use a tool
like **gitmine** to try to find *pain points* instead of entry points.

When I say "pain points", I mean code that changes often and also tends to 
change a lot. In general, this means that either, there is a whole lot 
of stuff going on in there, or is a really fragile part of the system, 
or what ever, *it's something that worth to take a look at* beacuse there
is a lot of action in there.

By using **gitmine** you will be able to tell which files changes 
often, who 've been working on those files, detect potencial refactors, 
and much more...

## How to install
Just run the instalation script.
```
./install
```
\*Note: You may have to add ~/bin to your path (manually).

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
This command is useful when you want to see who had worked on 
what. 

As well as **cmpf** you will see a list of file names and commits count 
but this time it'll be **filter by author**.

```
gitmine cmpf amiralles
```
### What been doing?
This command allows you to see what an author have been doing since a
given date.

```
# arguments:
# 'yyyy-MM-dd'
# author

gitmine wbd '2016-05-14' amiralles

```

### Show Commits Since .. Until
This command allows you to see a range of commits between two dates.
(You can also filter by author.)

```
# arguments:
# 'yyyy-MM-dd'
# 'yyyy-MM-dd'
# author

gitmine cmts '2016-05-14' '2016-08-08' amiralles

```

### Ref Count
This command indexes all classes on a given srouce tree and creates a list
of references to those classes by looking at every file in the codebase.

While is not 100% accurate, it will give you an
idea of how many dependencies meybe affected by changes on a particular file.

(I'd agree that if you say that if you are using and IDE, this feature has no sence at all ;))

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




