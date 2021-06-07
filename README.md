# Useful Powershell Commands

## Git
#### Local branch cleanup
Removes all merged local branches not named "develop" or "master"
```powershell
git for-each-ref --format '%(refname:short)' refs/heads --merged | ForEach-Object { If("develop","master" -notcontains $_) { git branch $_ -d } }
```

## Docker
#### Copy file from host to container
```powershell
docker cp C:\Users\MyUser\file.txt testcontainer:/home/user/file.txt
```

