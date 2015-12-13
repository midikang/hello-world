
# Permenant delete sensitive file from git repository history

# change to master branch
 git checkout master
 
# remove TopSecret.md from master branch

  git filter-branch --tree-filter 'rm -f TopSecret.md' HEAD
  
# change to development branch

  git checkout development
# remove TopSecret.md from development branch

  git filter-branch --tree-filter -f 'rm -f TopSecret.md' HEAD
  Cannot create a new backup.
  A previous backup already exists in refs/original/
  Force overwriting the backup with -f
  
# add parameter "-f" 

  git filter-branch --tree-filter 'rm -f TopSecret.md' -f HEAD
  Rewrite b55e8093b11cae0f43f33dc9a2aa76ed27db8262 (2/2)
  Ref 'refs/heads/development' was rewritten
