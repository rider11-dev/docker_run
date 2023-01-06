# 如果需要初始化或者升级数据库结构，需要指定profile为schema
docker compose --profile schema up -d
# 启动dolphinscheduler所有服务，指定profile为all
docker compose --profile all up -d

# 登录
-  http://localhost:12345/dolphinscheduler/ui
- admin,dolphinscheduler123



