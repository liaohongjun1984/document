# **多好信息科技有限公司培训计划**(第一版)
# **目录**
* * *
- [第一天](#第一天)
  1. 代码规范和命名习惯

    1.1. 数据库

    1.2. JAVA代码

# 第一天
* * *
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
