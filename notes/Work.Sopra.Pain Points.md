---
id: yo8diksbabv7mtibxeuuswc
title: Pain Points
desc: ''
updated: 1684762837030
created: 1679309795074
---

### Populating DB
With modelworld data use the FeatureTestsRunner, debug port is always 8000 with tomcat default

## Restore deleted file in Git
Find the last commit that affected the given path. As the file isn't in the HEAD commit, that previous commit must have deleted it.

`git rev-list -n 1 HEAD -- <file_path>`
Then checkout the version at the commit before, using the caret (^) symbol:

`git checkout <deleting_commit>^ -- <file_path>`
Or in one command, if $file is the file in question.

`git checkout $(git rev-list -n 1 HEAD -- "$file")^ -- "$file"`

### Rebasing
If the branch has moved ahead of where you are and this causes merge conflicts you want to:
- Change to master, in this case `support/8.47/dev` and git pull (can also do `git pull origin support/8.47/dev`)
- Then you want to `git rebase <master-branch>` and resolve the conflicts (there was a comment by lander I could potentially do `git pull --rebase <branch>` from my branch)
- Once rebased a `git status` will return the fact there are commit differences between my branch and the remote and ask for a `git pull` but instead you want to force push `git push -f` to override the remote with what is local

### Flyway error when running WFS
- Caused by migration change and model world lite runner needs rerunning
- To do this edit the run config of `ModelWorldLiteRunner` and `Modify Options` and add VM args and then input this `-javaagent:C:\Users\alexajones2\ide_resources\libs\aspectjweaver-1.9.5.jar -Xms256m -Xmx4096m -XX:+UseParallelGC -Djava.io.t=pdir=C:\tmp`

### Adding VM args to configurations Intellij
`-javaagent:C:\Users\alexajones2\ide_resources\libs\aspectjweaver-1.9.5.jar -Xms256m -Xmx4096m -XX:+UseParallelGC -Djava.io.tmpdir=C:\tmp`

### setterAspect error
When repopulating a db if this comes up it means you're lacking VM args for the populator, you also need to have `shorten command line` with `JAR manifest - java -cp classpath.jar className [args]` selected.

### Devidence (Acceptance Testing)
https://confluence.apak.com/live/pages/viewpage.action?spaceKey=WIKI&title=Acceptance+Testing