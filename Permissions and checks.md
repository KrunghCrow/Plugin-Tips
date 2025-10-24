Making your permissions is pretty simple
There are several options but this is what i like to use

The actual check
```cs
permission.UserHasPermission(player.UserIDString, perm)
```
* Registration : Regestering you permission during Init() after setting the permission.
```cs
        string Admin_Perm = "test.admin";

        void Init()
        {
            permission.RegisterPermission(Admin_Perm, this);
        }
```
* API : Setting up your shortcut
```cs
        bool HasPerm(BasePlayer player, string perm) { return permission.UserHasPermission(player.UserIDString, perm); }
```
* Calls and checking for permissions (Basic)
```cs
        void OnEntityTakeDamage(BaseAnimalNPC animal, HitInfo info)//example hook to see permission and warning notification for animals
        {
            BasePlayer player = info.InitiatorPlayer;

            if (animal == null || player == null || info == null) return;
            if (HasPerm(player, Warning_Perm))
            {
              // Do your thing
            }
            else
            {
              // Do your not to do thing
              return;
            }  
        }
```
