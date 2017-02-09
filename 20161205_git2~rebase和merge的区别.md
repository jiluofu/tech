**2016.12.05**

Suppose originally there were 3 commits, A,B,C:
![A-B-C](https://i.stack.imgur.com/lJRq7.png)

Then developer Dan created commit D, and developer Ed created commit E:
![A-B-C-D-E](https://i.stack.imgur.com/pK7Zb.png)

Obviously, this conflict should be resolved somehow. For this, there are 2 ways:

**MERGE**:
![A-B-C-D-E-M](https://i.stack.imgur.com/9Ul5w.png)
Both commits D and E are still here, but we create merge commit M that inherits changes from both D and E. However, this creates *diamond* shape, which many people find very confusing.

**REBASE**:
![A-B-C-D-E-R](https://i.stack.imgur.com/TvXuJ.png)

We create commit R, which actual file content is identical to that of merge commit M above. But, we get rid of commit E, like it never existed (denoted by dots - vanishing line). Because of this obliteration, E should be local to developer Ed and should have never been pushed to any other repository. Advantage of rebase is that *diamond* shape is avoided, and history stays nice straight line - most developers love that!

from:http://stackoverflow.com/questions/16666089/whats-the-difference-between-git-merge-and-git-rebase