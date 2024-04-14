 加载权限
    文件或数据库加载权限

获取网络信息

创建数据库
    初始化

创建合同处理程序

创建钱包处理程序

创建交易处理程序

创建新用户程序

创建gin网络路由
    设置路由
    运行server

修改日志：
func (km *KeyManager) StoreSharesToTheBlockchain(userID string, shares []string, networks []config.NetworkConfiguration) error {
	for i, share := range shares {
		fmt.Println("Share to be stored:", share, ", on chain:", networks[i].Network)

		// 使用 defer 来处理可能的错误
		defer func() {
			if r := recover(); r != nil {
				fmt.Println("Error storing share:", r)
			}
		}()

		middleware.StoreShares(networks[i], stringToBytes32(userID), share)
	}

	return nil // 返回 nil 表示操作成功
}