## 该项目使用idea ide编写

## 服务启动：    
* 需要本地安装maven版本3.0以上    
* mvn jetty:run    
* 训练模型
* mvn scala:run -Dlauncher=PojoExample
* mvn scala:run -Dlauncher=SparklingWaterDroplet

## 日志收集：    
* 发送数据到EventServer,该接口是标准rest API    
* curl -H "Content-Type: application/json" -X POST -d '{"appid": "test","context": {"deviceid": "XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX"}}' http://192.168.2.29:8181/receive/rest/install    
* 代码位置：    
* saas/EventServer/src/main/java/com/iaskdata/controller/RestController.java    

## 数据预测：    
* 该预测接口，使用app-consumer-loan生成的模型    
* http://127.0.0.1:8181/receive/predict?loan_amnt=10000&emp_length=5&home_ownership=RENT&annual_inc=60000&verification_status=verified&purpose=debt_consolidation&addr_state=FL&dti=3&delinq_2yrs=0&revol_util=35&total_acc=4&longest_credit_length=10    
* 代码位置：    
* saas/EventServer/src/main/java/com/iaskdata/controller/FunctionController.java    

## 模型训练：    
* 尚未实现    
* http://127.0.0.1:8181/receive/train    
* 代码位置：    
* saas/EventServer/src/main/java/com/iaskdata/controller/FunctionController.java    

## 关于vw的使用    
* 所有vw包在lib目录下    
  * config.h vwb版本文件     
  * vw_jni.lib mac下编译出来的版本     
  * vw-jni-8.1.2-SNAPSHOT.jar vw最新java文件夹编译出来的jar包    
* 关于vw的测试用例都在 saas/EventServer/src/test/java/vw 下面
* 运行测试用例必要条件
  * mvn clean 
  * mvn install
  * mvn test
* 如果修改了测试用例，只需要执行mvn test就可以检查运行是否正确了
