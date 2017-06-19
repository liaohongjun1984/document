# **多好信息科技有限公司培训计划**(第一版)
# **目录**
* * *
- [第一天+第二天](#第一天+第二天)
  1. [代码规范和命名习惯](#代码规范和命名习惯)
      + [数据库](#数据库)
      + [JAVA代码](#JAVA代码)
      + [service,core,helper等包的具体作用](#service,core,helper等包的具体作用)
  2. [公司代码框架和目录结构](#公司代码框架和目录结构)
- [第三天](#第三天)
  1. [mybatis自动生成的代码怎么和custom代码怎么配合使用](#mybatis自动生成的代码怎么和custom代码怎么配合使用)
  2. [redis的使用](#redis的使用)
- [第四天](#第四天)
  1. [微服务的概念和使用](#微服务的概念和使用)
  2. [svn，git的使用和服务的部署](#svn，git的使用和服务的部署)
- [第五天+第六天](#第五天+第六天)

# 第一天+第二天
## 代码规范和命名习惯
### 数据库
表和字段的命名一般都是以小写和下划线为主，所有的单词以下划线为分隔符，表的命名有些会以模块的缩写作为前缀。

例如
```
tc_order,tc_order_user,tc_order_service,tc_order_detail
```
等等等等 tc就是前缀，也是模块的的缩写。
### JAVA代码
package命名，package的命名一帮会以功能和模块去划分

例如
```JAVA
package com.idohoo.controller;
package com.idohoo.controller.order;
package com.idohoo.controller.pms;
package com.idohoo.controller.user;

package com.idohoo.service;
package com.idohoo.service.order;
package com.idohoo.service.pms;
package com.idohoo.service.user;
```
等等等等，具体的可以看代码里面是怎么去命名的

class类的命名，大驼峰命名法，一般会和业务或者数据库表有关例如，结尾以功能去划分。

方法命名，小驼峰命名法，一般会和业务有关，命名不要太长。

类变量的命名，一般会以下划线命名法，这个是因为要返回给前端使用。

方法变量的命名，一般是以小驼峰命名法。

注释怎么写，这个具体看下面的例子。

大括号的第一个{一般会跟在代码的最后面
```JAVA
public class TcOrderVO{
  /** 主键*/  //这个是类变量的注释
  private Integer tc_order_id;
  /** 订单编号*/
  private String tc_order_no;

  /**
   * getter 获取主键 这个是方法上面的注释
   * @author idohoo
   * @return 放回主键
   */
  public Integer getTc_order_id(){
    return this.tc_order_id;
  }
  /**
   * setter 获取主键 这个是方法上面的注释
   * @author idohoo
   * @param tc_order_id
   */
  public void setTc_order_id(Integer tc_order_id){
    this.tc_order_id = tc_order_id;
  }

  public String getTc_order_no(){
    return this.tc_order_no;
  }
  public void setTc_order_no(String tc_order_no){
    //这个是方法里面的注释
    //TODO author:idohoo TODO的注释一般要写上是谁写的以便后面修改的时候可以搜索到
    this.tc_order_no = tc_order_no;
  }
}
public interface TcOrderService{  
  TcOrderVO getVO(Integer tc_order_id);
}
public class TcOrderSerivceImpl implements TcOrderService{

  /**
   * 这种方法的命名就是用的小驼峰命名法
   * @author idohoo
   * @param tc_order_id
   * @return TcOrderVO
   */
  @Override
  public TcOrderVO getVO(Integer tc_order_id){
    //这种方法里面的变量命名就是用的小驼峰
    TcOrderVO tcOrderVO = new TcOrderVO();

    return tcOrderVO;
  }
}
public class TcOrderController{
}
```
### service,core,helper等包的具体作用
* interceptor 拦截器,相当于Filter(这个具体可以百度)。
* controller 控制器，所有url的入口，这里可以引用service,vo,util对入参和service的返回结果进行处理(这个具体可以百度)。
* service 服务 具体的业务处理的地方，这里可以引用dao,helper,core,vo,model,util层，访问持久层，对数据进行处理，再返回给controller层。
* dao 对mapper层和redis层进行一层封装，这里可以引用mapper,redis,model,util,model,vo。
* mapper 数据持久层，这里分autocode和custom,通过mybatis框架访问数据库，最底层。
* redis 对redis非关系数据库的访问,可以访问，model,vo,util。
* util 工具包，和业务无关的工具包，这个一般是写一些与项目无关的共用代码。
* helper 工具包，和util最大的区别在于这个是和业务有关，一帮是跟着项目走,这里可以引用util,vo,model。
* core 工具包，和util和helper最大的区别在于core包会访问dao层，对业务逻辑进行处理。和service层一样，不过这个地方是将service层里面的代码抽出来形成的一层。
* model 这个地方是放和数据库表映射的模型
* vo 对外的value object
## 公司代码框架和目录结构
具体的demo去可以HR拿，这个就不放在这里了。
# 第三天
## mybatis自动生成的代码怎么和custom代码怎么配合使用
这里差一个demo
## redis的使用
这里差一个demo
# 第四天
## 微服务的概念和使用
[spring-boot-cloud](https://github.com/idohoo/spring-boot-cloud-demo "spring-boot-cloud的demo")
## svn，git的使用和服务的部署
具体的服务器地址和帐号密码可以找HR要
# 第五天+第六天
这个地方到时候可以补充一个案例，对以上所学到的东西做一个总结，也就是写一个实例，包括代码+项目部署。
