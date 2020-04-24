### 共有ディレクトリ作る
#### 管理者権限でCMD実行

```
C:\WINDOWS\system32>"C:\Program Files\Oracle\VirtualBox\VBoxManage.exe" setextradata [vm name] VBoxInternal2/SharedFoldersEnableSymlinksCreate/[dir1] 1
C:\WINDOWS\system32>"C:\Program Files\Oracle\VirtualBox\VBoxManage.exe" setextradata [vm name] VBoxInternal2/SharedFoldersEnableSymlinksCreate/[dir2] 1

C:\WINDOWS\system32>"C:\Program Files\Oracle\VirtualBox\VBoxManage.exe" getextradata nova enumerate
Key: GUI/LastCloseAction, Value: PowerOff
Key: GUI/LastNormalWindowPosition, Value: 737,148,720,442
Key: VBoxInternal2/SharedFoldersEnableSymlinksCreate/dir1, Value: 1
Key: VBoxInternal2/SharedFoldersEnableSymlinksCreate/dir2, Value: 1

cd C:\Windows\system32
fsutil behavior set SymlinkEvaluation L2L:1 R2R:1 L2R:1 R2L:1
```

#### 管理者権限でVM実行
```bash
ln -s /media/sf_xxx_api/fuel/app/classes/library   /media/sf_xxx_admin/fuel/app/classes/library
ln -s /media/sf_xxx_api/fuel/app/classes/model     /media/sf_xxx_admin/fuel/app/classes/model
```
