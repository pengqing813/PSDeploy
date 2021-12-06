# PowerShell Deploy

自动部署

## 安装

把此代码下载或通过git clone到本地
然后在目录下面以管理员方式运行Install.ps1

```powershell
cd .\ZEQP-PSDeploy
Install.ps1
```

## 自动编译然后发布到指定服务器IIS站点

```powershell
#前端
Start-Deploy -ComputerName 127.0.0.1 -WebSiteName DefaultWebSite -WebSitePort 8051 -ScriptBlock { npm run build:live } -OutputPath .\dist\

#后端
Start-Deploy -ComputerName 127.0.0.1 -WebSiteName DefaultWebSite -WebSitePort 8053 -ScriptBlock { param($o) dotnet publish -o $o -c "Release" --no-self-contained -v m --nologo } -OutputPath .\bin\publish\
```

## 自动编译然后发布为服务

```powershell
#后端
Start-DeploySvc -ComputerName 127.0.0.1 -ServiceName DefaultService -ServicePort 8054
```
