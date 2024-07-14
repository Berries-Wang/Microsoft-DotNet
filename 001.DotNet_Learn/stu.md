1. 值类型
2. .net runtime提供: automatic memory management via a garbage collector.  
3. 反射
4. 包管理器: NuGet
5. 异常处理
6. 面向对象
7. 类型系统: 单一继承


## .net生态
.net有多种实现: 因为历史原因 和  技术原因

- .NET Framework : 最初的.net,仅提供了windows平台运行能力
- Mono : 原始社区和开源.net,跨平台实现的.NET Framework
- .NET (Core)  : 现在.net ,跨平台和开源实现，积极支持 Linux , Macos , Windows


wei@Berries-Wang:~/WorkSpace/Open_Source/Microsoft-DotNet/000.SOURCE_CODE/000.DotNet-RELEASE-V8.0.7/dotnet-8.0.7/artifacts/x64/Release/wei-sdk$ ./dotnet  new console -o wei_demo
The template "Console App" was created successfully.

Processing post-creation actions...
Restoring /home/wei/WorkSpace/Open_Source/Microsoft-DotNet/000.SOURCE_CODE/000.DotNet-RELEASE-V8.0.7/dotnet-8.0.7/artifacts/x64/Release/wei-sdk/wei_demo/wei_demo.csproj:
/home/wei/WorkSpace/Open_Source/Microsoft-DotNet/000.SOURCE_CODE/000.DotNet-RELEASE-V8.0.7/dotnet-8.0.7/Directory.Build.props(9,3): error : Could not resolve SDK "Microsoft.DotNet.Arcade.Sdk". Exactly one of the probing messages below indicates why we could not resolve the SDK. Investigate and resolve that message to correctly specify the SDK.
/home/wei/WorkSpace/Open_Source/Microsoft-DotNet/000.SOURCE_CODE/000.DotNet-RELEASE-V8.0.7/dotnet-8.0.7/Directory.Build.props(9,3): error :   SDK resolver "Microsoft.DotNet.MSBuildWorkloadSdkResolver" returned null.
/home/wei/WorkSpace/Open_Source/Microsoft-DotNet/000.SOURCE_CODE/000.DotNet-RELEASE-V8.0.7/dotnet-8.0.7/Directory.Build.props(9,3): error :   Unable to find package Microsoft.DotNet.Arcade.Sdk. No packages exist with this id in source(s): dotnet-public
/home/wei/WorkSpace/Open_Source/Microsoft-DotNet/000.SOURCE_CODE/000.DotNet-RELEASE-V8.0.7/dotnet-8.0.7/Directory.Build.props(9,3): error :   MSB4276: The default SDK resolver failed to resolve SDK "Microsoft.DotNet.Arcade.Sdk" because directory "/home/wei/WorkSpace/Open_Source/Microsoft-DotNet/000.SOURCE_CODE/000.DotNet-RELEASE-V8.0.7/dotnet-8.0.7/artifacts/x64/Release/wei-sdk/sdk/8.0.107/Sdks/Microsoft.DotNet.Arcade.Sdk/Sdk" did not exist.
/home/wei/WorkSpace/Open_Source/Microsoft-DotNet/000.SOURCE_CODE/000.DotNet-RELEASE-V8.0.7/dotnet-8.0.7/Directory.Build.props(9,78): error MSB4236: The SDK 'Microsoft.DotNet.Arcade.Sdk' specified could not be found. [/home/wei/WorkSpace/Open_Source/Microsoft-DotNet/000.SOURCE_CODE/000.DotNet-RELEASE-V8.0.7/dotnet-8.0.7/artifacts/x64/Release/wei-sdk/wei_demo/wei_demo.csproj]
Restore failed.
Post action failed.
Manual instructions: Run 'dotnet restore'


./build.sh --clean-while-building  --release-manifest  release.json