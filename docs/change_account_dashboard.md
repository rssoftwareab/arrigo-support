# Change the dashboard for the Account in Arrigo 1.0.299 or higher



To change the Account (House button) to a custom dashboard, a new object needs to be added to the Arrigo-folder template file.

Create a new dashboard with the ArrigoFolder/ArrigoFolderViews tools and save the files to shared:.

Open the template file proj:\Arrigo\\.folder.json

Add these lines above the existing configurations in the file

{
		"type":["Account"],
		"rwaf":"path to the new rwaf file"
}

The file should look something like this:

```
[
{
		"type":["Account"],
		"rwaf":"Shared:\\Arrigo\\FolderTypes\\account.rwaf"
},
{
		"rwaf":"Shared:\\Arrigo\\FolderTypes\\default.rwaf"
}
]
```

Restart the EXOscada (this not needed in the up coming stable version)



















