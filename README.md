## ShowCmdLineArgs

ShowCmdLineArgs is a simple AVR for .NET program that shows the command line arguments passed to it. You can run it directly from the command line (as shown in the figure below) or launch it with OSEXEC from AVR. 

![](https://asna.com/filebin/marketing/article-figures/show-cmd-line-args.png)

There isn't much code in ShowCmdLineArgs. It uses .NET's `Environment` namespace's [`GetCommandLineArgs`](https://docs.microsoft.com/en-us/dotnet/api/system.environment.getcommandlineargs?view=netframework-4.7.1#System_Environment_GetCommandLineArgs) method to fetch the command line arguments. `GetCommandLineArgs` always has the name of the currently-running executable in the zeroth argument, then the other arguments contain the corresponding command line arguments. 

`GetCommandLineArgs` returns the values fetch as an array of strings. This array is assigned to a `ListBox` by assigning it to the `ListBox's` `DataSource` property. 

    DclArray CmdLineArgs Type(*String) Rank(1) 

    BegSr Form1_Load Access(*Private) Event(*this.Load)
        DclSrParm sender *Object
        DclSrParm e System.EventArgs

        // GetCommandLineArgs always returns the currently-running executable
        // as the zeroth argument. 
        CmdLineArgs = Environment.GetCommandLineArgs()
        
        listboxCmdLineArgs.DataSource = CmdLineArgs
    EndSr

    BegSr buttonExit_Click Access(*Private) Event(*this.buttonExit.Click)
        DclSrParm sender Type(*Object)
        DclSrParm e Type(System.EventArgs)

        *This.Close()
    EndSr
