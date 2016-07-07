## Feature branching

1. Create a new feature branch called 'squash_some_bugs'
2. Edit 'bugs.rb' and remove all the bugs.
3. Commit
4. Push
5. Commands

----------
```
git checkout -b squash_some_bugs
# Edit `bugs.rb`
git status
git add bugs.rb
git commit -m 'Fix some buggy code'
git push origin squash_some_bugs
```
