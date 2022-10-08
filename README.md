# -开机自启动的权限维持---
\HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows\CurrentVersion\Run  windows开机自启动键值
RegCreateKeyEx windows给我们提供的注册表操作api


RegCreateKeyExA功能(winreg.h)


创建指定登记册的关键。 如果关键已经存在的功能打开它。 注意，关键的名字不敏感。

执行事务注册的操作上的一个关键，调 RegCreateKeyTransacted 功能。

应用程序的备份或恢复系统的状态，包括系统的文件和注册表荨麻疹应使用 积影复制服务 ，而不是注册的功能。
语法
C++

LSTATUS RegCreateKeyExA(
  [in]            HKEY                        hKey,
  [in]            LPCSTR                      lpSubKey,
                  DWORD                       Reserved,
  [in, optional]  LPSTR                       lpClass,
  [in]            DWORD                       dwOptions,
  [in]            REGSAM                      samDesired,
  [in, optional]  const LPSECURITY_ATTRIBUTES lpSecurityAttributes,
  [out]           PHKEY                       phkResult,
  [out, optional] LPDWORD                     lpdwDisposition
);

参数

[in] hKey

一个处理一个开放注册的关键。 叫进程必须具有KEY_CREATE_SUB_KEY访问的关键。 更多信息，请参阅 登记册关键的安全和访问权限 .

访问为关键的创造是对安全描述的登记册的关键，不对访问掩指定的当处理获得。 因此，即使 hKey 开幕 samDesired 的KEY_READ，它可用于操作，修改登记册，如果允许通过其安全的描述符。

这种处理返回的 RegCreateKeyEx 或 ： 功能，或者它可以是以下之一 预先定义的钥匙 :

    注册表 
    HKEY_CURRENT_CONFIG 
    注册表 
    此 
    项 

[in] lpSubKey

名称的一个子项，这一功能打开或创建的。 子项规定必须一个子项关键的标识通过 hKey 参数；它可以达到32个级别深，在注册表中树。 更多信息，关键的姓名，请参阅 结构的注册表 .

如果 lpSubKey 是指向空串， phkResult 收到一个新的处理的关键指定的 hKey .

此参数不能 NULL .

Reserved

此参数被保留，并必须为零。

[in, optional] lpClass

用户定义的类型的这个关键。 这种参数可能会被忽略。 这种参数可以 NULL .

[in] dwOptions

这种参数可以以下一种价值观。
值 	意思

REG_OPTION_BACKUP_RESTORE
0x00000004L

	如果这标志设置、功能忽略 samDesired 参数，并尝试开关键的访问所需的备份和恢复的关键。 如果调线有SE_BACKUP_NAME特权启用，关键的是打开与ACCESS_SYSTEM_SECURITY和KEY_READ的访问权限。 如果调线有SE_RESTORE_NAME特权启用，开始使用Windows Vista，关键的是打开与ACCESS_SYSTEM_SECURITY，删除和KEY_WRITE的访问权限。 如果双方权限的启用，关键的联合访问权利的权限。 更多信息，请参阅 运行具有特殊权限 .

REG_OPTION_CREATE_LINK
0x00000002L

	
注意 注册的象征性的链接，只应当用于应用程序兼容性的时候 绝对 必要的。
 
这把钥匙是一个象征性的链接。 目标道路分配给L"SymbolicLinkValue"价值的关键。 目标的路径必须是一个绝对登记册的道路。

REG_OPTION_NON_VOLATILE
0x00000000L

	这键不是挥发性；这是默认的。 信息储存在一个文件，而是保留在系统重新启动。 的 RegSaveKey 功能节省键，都不易挥发。

REG_OPTION_VOLATILE
0x00000001L

	所有的钥匙创建的功能被挥发性的。 信息存储器中存储和不保留在相应的登记册蜂巢被卸载。 为 此 ，发生这种情况只有当该系统中发起一个全关闭。 对注册表键装的 RegLoadKey 功能，这时会发生相应的 RegUnLoadKey 执行。 的 RegSaveKey 功能不易挥发的钥匙。 这个标志是忽略键已经存在。
注意到 在一个用户选择的关闭， 一个快速启动关闭是默认的行为的系统。 
