## Renci.SshNet.Async [![Build status](https://ci.appveyor.com/api/projects/status/wbusmehom3aub79y?svg=true)](https://ci.appveyor.com/project/JohnTheGr8/renci-sshnet-async) [![NuGet](https://img.shields.io/nuget/v/Renci.SshNet.Async.svg?style=flat)](https://www.nuget.org/packages/Renci.SshNet.Async)

#### About
A collection of extensions for SSH.NET that implement the `Task-based Asynchronous Pattern` from the originally implemented `Asynchronous Programming Model`

#### Install
You can install Renci.SshNet.Async from [Nuget](https://www.nuget.org/packages/Renci.SshNet.Async):

``` powershell
	PM> Install-Package Renci.SshNet.Async
```

#### Usage

The code sample below demonstrates how the extension methods are used.

``` cs
	// initialize client and connect like you normally would
	var client = new SftpClient("host", "username", "password");
	client.Connect();

	// await a directory listing
	var listing = await client.ListDirectoryAsync(".");

	// await a file upload
	using (var localStream = File.OpenRead("path_to_local_file"))
	{
		await client.UploadAsync(localStream, "upload_path");
	}

	// disconnect like you normally would
	client.Disconnect();
```