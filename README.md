# mani_idl
idl文件定义，mani服务简述
(请用txt模式阅读，非md格式)


一. 服务架构:
微信小程序前端服务：editpro

后端服务:
    gin_mani_crm_api: api聚合层服务
    gin_mani_user: 用户服务（用户信息，用户收藏，用户推荐，用户浏览历史记录）
    gin_mani_center: 模型服务（模型行为，规则定义/转化）
    gin_mani_engine: 引擎服务（执行模型任务，url转化） 

二. 基础架构拓扑：
                      editpro [mpvue 框架]
                         |
                         | (http通信)
                         |
                   gin_mani_crm_api 
                         ｜
                         ｜
                         ｜(rpc通信)                     
     ---------------------------------------------------      
     |                    |     [grpc 框架]              |
     |                    |                             |
     |                    |                             |
gin_mani_user ------- gin_mani_center --------------- gin_mani_engine
     |                    |                             ｜
     |                    |                             ｜
     |                  redis数据库                    redis数据库(简单作为消息队列)
   mysql数据库             |  
                          |
                        mysql 数据库
                 
