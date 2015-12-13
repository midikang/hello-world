
# Permenant delete sensitive file from git repository history
git filter-branch --tree-filter 'rm -f TopSecret.md' HEAD
