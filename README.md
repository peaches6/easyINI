# easyINI


Parse INI files using the Windows API.

You can also:
  - Check if a key exists
  - Delete keys
  - Delete sections
  - Get all sections
  
To add:
  - ~~Get all sections (into array)~~

> Feel free to use this in
> any personal projects
> without attribution


### Usage and examples

Creates a new INI file in your current dir named after the executing assembly
```csharp
var MyIni = new IniFile();
```
Creates an ini file in current dir with specified name
```csharp
var MyIni = new IniFile("settings.ini");
```

Creates a new ini file in specified directory
```csharp
var MyIni = new IniFile(@"C:\settings.ini");
```

Easy start
```csharp 
MyIni.Write("Key", "Value", "Section (optional)");
MyIni.Read("Key", "Section (only state if it's not default one)");
```
    
Writing to an INI file:
    
Writing to file with default section (name of executable)
```csharp
MyIni.Write("DefaultValue", "40");
MyIni.Write("userName", "admin");
```

Creates a file like this:

	[EXE NAME]
	DefaultValue=40
	userName=admin

Writing to file with specified section
```csharp
MyIni.Write("DefaultValue", "40", "VALUES");
MyIni.Write("userName", "admin", "USER");
```

Creates a file like this:

	[VALUES]
	DefaultValue=40
	[USER]
	userName=admin
    
Reading from INI file:
    
Can explicitly state variable type or use var instead
```csharp
string DefaultValue = MyIni.Read("DefaultValue");
```
or
```csharp
int DefaultValue = Convert.ToInt32(MyIni.Read("DefaultValue"));


string username = MyIni.Read("userName");

string[] allSections = MyINI.GetSectionNames();
    
```
Checking if key exists
    
    Easy start
    
```csharp
bool keyExist = MyIni.KeyExists("Key", "Section (only state if it's not default one)");

if(!MyIni.KeyExists("DefaultValue", "VALUES"))
{
MyIni.Write("DefaultValue", "40", "VALUES");
}
```

Deleting keys and sections:

```csharp
MyIni.DeleteKey("DefaultValue", "VALUES");
MyIni.DeleteSection("VALUES");
```
