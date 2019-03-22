Today, I tried adding SSH Keys into my git.
For that I followed the documentation given on Github. I must confess that documentation given in Github is pretty cool and if you follow complete discussion, its easy to add the same. Adding ssh keys requires some by default commands and we should then add the same key by copying the matter present in my .ssh file and copying it into my github ssh keys section.
I then tried to push my changes and whoo.. Something didn't work. Pushing the commit changes was still requiring username and password. So I came to a solution and that was to change the remote to that of ssh keys.The following command changed it,
```
git remote set-url origin git@github.com:username/server-repository-name.git

```


And whoa it worked and now I did that for all repositories present. Now I doesn't need to add username and password each time while pushing changes.
