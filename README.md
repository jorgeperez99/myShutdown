# myShutdown
This is a console application that puts a computer to sleep. 
You can pass 4 parameters to make the pc **sleep**, **hibernate**, 
**shutdown** or **restart**.  

The reason i created this application was because i removed all the buttons from windows so my family stops putting the computer to sleep.  This affected me because i was unable to rdp to it, however i removed the buttons for myself too, so i needed a way to put computer to sleep.

Use without parameter or pass **sleep** to make computer sleep

```
myShutdown.exe 
myShutdown.exe sleep
```
Pass **shutdown** to make computer **shutdown**
```
myShutdown.exe shutdown
```
Pass **restart** to make computer **restart**
```
myShutdown.exe restart
```
Pass **hybernate** to make computer **hybernate**
```
myShutdown.exe hybernate
```
This is what the main method looks like.
```
static void Main(string[] args) {
    if (args.Length > 0) {
        var shutdownType = args[0];
    } else {
        shutDownType = shutDownTypeEnum.sleep;
    }
    switch (shutDownType) {
        case shutDownTypeEnum.sleep:
            Application.SetSuspendState(PowerState.Suspend, true, true);
            break;
        case shutDownTypeEnum.shutdown:
            System.Diagnostics.Process.Start("shutdown.exe", "-s 0");
            break;
        case shutDownTypeEnum.restart:
            System.Diagnostics.Process.Start("shutdown.exe", "-r");
            break;
        default:
            Application.SetSuspendState(PowerState.Hibernate, true, true);
            break;
    }
}
```
