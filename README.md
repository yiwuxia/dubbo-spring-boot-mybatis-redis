yiwuxia
# dubbo-spring-boot-mybatis-redis
通过dubbo+spring boot+mybatis+redis等主流技术搭建成一套分布式服务框架

项目介绍：

1、首先安装zookeeper+redis；

2、dearbinge-data-provider服务提供者项目的资源文件dubbo-spring-mybatis.xml下配置zookeeper地址；

3、dearbinge-openapi服务消费者的资源文件dubbo-services.xml下配置zookeeper地址，然后在application.properties下配置redis地址；

4、dearbinge-security服务消费者的资源文件dubbo-services.xml下配置zookeeper地址；

5、建立数据库文件cloudplate，创建`t_security`表单元素

脚本如下：
/*
Navicat MySQL Data Transfer

Source Server         : 192.168.1.118
Source Server Version : 50173
Source Host           : 192.168.1.118:3306
Source Database       : cloudplate

Target Server Type    : MYSQL
Target Server Version : 50173
File Encoding         : 65001

Date: 2016-04-05 17:50:09
*/

SET FOREIGN_KEY_CHECKS=0;

-- ----------------------------
-- Table structure for t_security
-- ----------------------------
DROP TABLE IF EXISTS `t_security`;
CREATE TABLE `t_security` (
  `f_SecurityKey` varchar(50) NOT NULL DEFAULT '',
  `f_SecurityValue` varchar(255) DEFAULT NULL,
  `f_MerchantId` varchar(255) DEFAULT NULL,
  `f_Tag` varchar(10) DEFAULT NULL,
  `f_IsDelete` int(11) DEFAULT NULL,
  `f_CreateUser` varchar(50) DEFAULT NULL,
  `f_CreateTime` date DEFAULT NULL,
  `f_UpdateUser` varchar(50) DEFAULT NULL,
  `f_UpdateTime` date DEFAULT NULL,
  `f_Remark` varchar(100) DEFAULT NULL,
  PRIMARY KEY (`f_SecurityKey`),
  KEY `FK_MERCHANTID` (`f_MerchantId`)
) ENGINE=MyISAM DEFAULT CHARSET=latin1;

-- ----------------------------
-- Records of t_security
-- ----------------------------
INSERT INTO `t_security` VALUES ('0eca8f5373ca4866aec2f8e9d9367104', '14318527b13840c2a4af63fef52c2d6e', '323202320202201509080001', '1', '1', null, null, null, null, '????');

6、启动dearbinge-data-provider项目下的mainloader注册服务提供者；

7、启动dearbinge-openapi项目下的App注册服务消费者；

8、整个项目即可完整运行。
