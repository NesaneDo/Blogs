# 使用 Spring Boot + MyBatis 一对多查询

1. 实体类 **Order** 和 **Clothes**

   ```java
   
   import java.math.BigDecimal;
   import java.sql.Timestamp;
   import java.util.List;
   
   /**
    * 订单表
    */
   public class Order extends BaseModel {
       private Integer id;
       private String number; // 订单号
       private String phone; // 用户电话
       private String place; // 取送衣地址
       private Timestamp createTime; // 订单创建时间
       private Timestamp finishTime; // 完成时间
       private Integer result; // 本次订单的完成结果：交易中 or 交易完成
       private Integer orderStatus; // 订单状态
       private BigDecimal amount; // 本订单金额
       private String remark; // 备注，如交易失败可填写原因
       private List<Clothes> clothes; // 一对多的订单详情
   
       @Override
       public String toString() {
           return "订单信息{" +
                   "ID=" + id +
                   ", 订单号='" + number + '\'' +
                   ", 用户电话号码='" + phone + '\'' +
                   ", 取送衣地址='" + place + '\'' +
                   ", 创建时间=" + createTime +
                   ", 完成时间=" + finishTime +
                   ", 订单结果='" + ORDER_RES[result] + '\'' +
                   ", 订单状态=" + ORDER_STATUS[orderStatus] +
                   ", 金额= " + amount.floatValue() + " 元" +
                   ", 备注= " + remark +
                   '}';
       }
   
       public String getRemarkUpdateDesc() {
           return "订单信息{" +
                   "ID=" + id +
                   ", 订单号='" + number + '\'' +
                   ", 用户电话号码='" + phone + '\'' +
                   ", 备注= " + remark +
                   '}';
       }
   
       public Order() {
       }
   
       public Order(String number, String phone, String place, Timestamp createTime, Timestamp finishTime, Integer result, Integer orderStatus, BigDecimal amount, String remark) {
           this.number = number;
           this.phone = phone;
           this.place = place;
           this.createTime = createTime;
           this.finishTime = finishTime;
           this.result = result;
           this.orderStatus = orderStatus;
           this.amount = amount;
           this.remark = remark;
       }
   
       public Integer getId() {
           return id;
       }
   
       public void setId(Integer id) {
           this.id = id;
       }
   
       public String getNumber() {
           return number;
       }
   
       public void setNumber(String number) {
           this.number = number;
       }
   
       public String getPhone() {
           return phone;
       }
   
       public void setPhone(String phone) {
           this.phone = phone;
       }
   
       public String getPlace() {
           return place;
       }
   
       public void setPlace(String place) {
           this.place = place;
       }
   
       public Timestamp getCreateTime() {
           return createTime;
       }
   
       public void setCreateTime(Timestamp createTime) {
           this.createTime = createTime;
       }
   
       public Timestamp getFinishTime() {
           return finishTime;
       }
   
       public void setFinishTime(Timestamp finishTime) {
           this.finishTime = finishTime;
       }
   
       public Integer getResult() {
           return result;
       }
   
       public void setResult(Integer result) {
           this.result = result;
       }
   
       public Integer getOrderStatus() {
           return orderStatus;
       }
   
       public void setOrderStatus(Integer orderStatus) {
           this.orderStatus = orderStatus;
       }
   
       public BigDecimal getAmount() {
           return amount;
       }
   
       public void setAmount(BigDecimal amount) {
           this.amount = amount;
       }
   
       public String getRemark() {
           return remark;
       }
   
       public void setRemark(String remark) {
           this.remark = remark;
       }
   
       public List<Clothes> getClothes() {
           return clothes;
       }
   
       public void setClothes(List<Clothes> clothes) {
           this.clothes = clothes;
       }
   }
   
   ```

   ```java
   
   /**
    * 单件衣物信息
    */
   public class Clothes extends BaseModel{
       private Integer id;
       private Integer orderId; // 订单id
       private Integer categoryId; // 衣物类别
       private Integer holderNumber; // 格架号
       private String name; // 衣物名称
       private Integer count; // 件数
       private String color; // 衣物颜色
       private String size; // 衣物尺寸
       private Integer washStatus; // 衣物当前的洗涤状态
       private String remark; // 备注
   
       @Override
       public String toString() {
           return "衣物信息{" +
                   "ID=" + id +
                   ", 订单ID=" + orderId +
                   ", 衣物名称='" + name + '\'' +
                   ", 衣物类别=" + categoryId +
                   ", 件数=" + count +
                   ", 颜色='" + color + '\'' +
                   ", 尺寸='" + size + '\'' +
                   ", 所在格架号='" + holderNumber + '\'' +
                   ", 洗涤状态='" + WASH_STATUS[washStatus] + '\'' +
                   ", 备注='" + remark + '\'' +
                   '}';
       }
   
       public Clothes() {
       }
   
       public Clothes(Integer orderId, Integer categoryId, Integer holderNumber, String name, Integer count, String color, String size, Integer washStatus, String remark) {
           this.orderId = orderId;
           this.categoryId = categoryId;
           this.holderNumber = holderNumber;
           this.name = name;
           this.count = count;
           this.color = color;
           this.size = size;
           this.washStatus = washStatus;
           this.remark = remark;
       }
   
       public Integer getId() {
           return id;
       }
   
       public void setId(Integer id) {
           this.id = id;
       }
   
       public Integer getOrderId() {
           return orderId;
       }
   
       public void setOrderId(Integer orderId) {
           this.orderId = orderId;
       }
   
       public Integer getCategoryId() {
           return categoryId;
       }
   
       public void setCategoryId(Integer categoryId) {
           this.categoryId = categoryId;
       }
   
       public Integer getHolderNumber() {
           return holderNumber;
       }
   
       public void setHolderNumber(Integer holderNumber) {
           this.holderNumber = holderNumber;
       }
   
       public String getName() {
           return name;
       }
   
       public void setName(String name) {
           this.name = name;
       }
   
       public Integer getCount() {
           return count;
       }
   
       public void setCount(Integer count) {
           this.count = count;
       }
   
       public String getColor() {
           return color;
       }
   
       public void setColor(String color) {
           this.color = color;
       }
   
       public String getSize() {
           return size;
       }
   
       public void setSize(String size) {
           this.size = size;
       }
   
       public Integer getWashStatus() {
           return washStatus;
       }
   
       public void setWashStatus(Integer washStatus) {
           this.washStatus = washStatus;
       }
   
       public String getRemark() {
           return remark;
       }
   
       public void setRemark(String remark) {
           this.remark = remark;
       }
   }
   
   ```

   

2. **Mapper.xml**

   ```xml
   <select id="getPageTypeOrders" resultMap="orderMap">
           select * from `order` o left join `clothes` c on o.id = c.orderId where `phone` like #{phone} and `result` = #{result} limit #{offset},#{limit};
       </select>
       <resultMap type="com.rondo.graduation.bean.Order" id="orderMap">
           <id property="id" column="id"/>
           <result property="number" column="number"/>
           <result property="phone" column="phone"/>
           <result property="place" column="place"/>
           <result property="createTime" column="createTime"/>
           <result property="finishTime" column="finishTime"/>
           <result property="result" column="result"/>
           <result property="orderStatus" column="orderStatus"/>
           <result property="amount" column="amount"/>
           <result property="remark" column="remark"/>
           <collection property="clothes" ofType="com.rondo.graduation.bean.Clothes">
               <result property="categoryId" column="categoryId"/>
               <result property="holderNumber" column="holderNumber"/>
               <result property="orderId" column="orderId"/>
               <result property="name" column="name"/>
               <result property="count" column="count"/>
               <result property="color" column="color"/>
               <result property="size" column="size"/>
               <result property="washStatus" column="washStatus"/>
               <result property="remark" column="remark"/>
           </collection>
       </resultMap>
   ```

   