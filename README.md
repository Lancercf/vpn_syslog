# vpn_syslog



### 要件定义：


通过指定参数(IP,用户名等)，取得相关syslog信息。



### 概要功能一览：

一：访问控制  
二：数据查询  
三：数据导出




### REST 接口说明：


#### 一：访问授权


    功能概要1 :  取得授权Key
    输入：    {
               用户名，
               密码
              }
    输出 :                
              0.成功： 
              {
                      授权KEY
              }
             -1.失败：错误信息(Error Message): 
              {
                       001：非法用户
                       002：密码错误   
              }


    功能概要2 :  验证授权Key是否过期
    输入：    {
                      授权KEY                     
              }
    输出：  
              0.成功：返回状态码
              {
                     0：授权有效 ,
               }

              -1.失败：错误信息(Error Message): 
              {
                      001：Key为空
                      002：Key无效    
                      003：授权失败（5分钟有效期）
               }


#### 二：数据查询

    功能概要1:   根据IP地址查找用户名。
    入力参数:         {
                           1.IP
                           2.返回项目件数(N:指定件数N， 0：全部)
                           3.开始时间，结束时间。
                           4.查询key。
                       }

    出力参数:     0.成功：.返回结果List
                       {
                          用户名，
                          登录时间，
                          动作(登录，退出)，
                          动作结果（成功，失败）
                          IP，
                          接口，
                          登录方式，
                          认证服务，
                          认证类型，
                          无效用户或用户超时
                       }                         
          
                       -1.失败：错误信息(Error Message)
                       {
                          001：IP空
                          002：IP格式非法
                          003：无效Key
                        }


    功能概要2:   根据用户名查找IP地址。
    入力参数:          {
                           1.用户名
                           2.返回项目件数(N:指定件数， 0：全部)
                           3.开始时间，结束时间。
                           4.查询key。
                       }

    出力参数:     0.成功：返回结果List
                       {
                          用户名，
                          登录时间，
                          动作(登录，退出)，
                          动作结果（成功，失败）
                          IP，
                          接口，
                          登录方式，
                          认证服务，
                          认证类型，
                          无效用户或用户超时
                       }                         
          
                       -1.失败：错误信息(Error Message)
                       {
                          001：用户空
                          002：用户名无效
                          003：无效Key
                        }

    功能概要3:   根据用户名查找操作系统版本。
    入力参数:     1.用户名
                       2.返回项目件数(N:指定件数， 0：全部)
                       3.开始时间，结束时间。
                       4.查询key。

    出力参数:     0.成功：返回结果List
                       {
                          用户名，
                          登录时间，
                          动作(登录，退出)，
                          动作结果（成功，失败）
                          NC IP，
                          认证类型，
                          操作系统版本
                       }                         
          
                       -1.失败：错误信息(Error Message)
                       {
                          001：用户空
                          002：用户句无效 
                          003：无效Key
                       }


#### 三：数据导出

    功能概要1:   用户名导出所有相关信息，到CSV。
    入力参数:         {
                           1.IP
                           2.返回项目件数(N:指定件数， 0：全部)
                           3.开始时间，结束时间。
                           4.查询key
                       }

    出力参数:     0.成功：.返回结果List
                       {
                          用户名，
                          登录时间，
                          动作(登录，退出)，
                          动作结果（成功，失败）
                          IP，
                          接口，
                          登录方式，
                          认证服务，
                          认证类型，
                          无效用户或用户超时，
                          操作系统类似
                       }                         
          
                       -1.失败：错误信息(Error Message)
                       {
                          001：用户空
                          002：无效用户名
                          003：无效Key
                        }
