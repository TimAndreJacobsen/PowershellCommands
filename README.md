# Useful Powershell Commands

## Git
#### Local branch cleanup
Removes all merged local branches not named "develop" or "master"
```powershell
git for-each-ref --format '%(refname:short)' refs/heads --merged | ForEach-Object { If("develop","master" -notcontains $_) { git branch $_ -d } }
```
Alternative that removes all branches branches gone on origin only if merged
```
git fetch -p

git branch -v |
  #find ones marked [gone], capture branchName
  select-string -Pattern '^  (?<branchName>\S+)\s+\w+ \[gone\]' | 
  foreach-object{ 
     #delete the captured branchname.
     git branch -D $_.Matches[0].Groups['branchName']
  }
```

## Docker
#### Copy file from host to container
```powershell
docker cp C:\Users\MyUser\file.txt testcontainer:/home/user/file.txt
```

