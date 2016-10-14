---
layout: post
title: 数据库_greenDAO
tags:
- android
categories: boatt
description: 数据库_greenDAO.
---
##  数据库_greenDAO
数据库_greenDAO

<!-- more -->
## 日志详情

- 主页: [https://github.com/greenrobot/greenDAO](https://github.com/greenrobot/greenDAO)

- 配置: 添加以下依赖

  - compile 'de.greenrobot:greendao:2.1.0'
  - compile 'de.greenrobot:greendao-generator:2.1.0'

- 用途: 操作数据库

- 优点: 

  - ![Logo](static/greenDAO.png)
  - 性能最大化,内存开销最小化
  - 易于使用的API
  - 为Android进行高度优化

- 使用步骤

  1. 创建自定义的DAOGenerater,指定数据库相关配置并生成相关类

     ```
     public class CustomDAOGenerater {
         public static void main(String[] args) throws Exception {
             // 第一个参数为数据库版本
             //第二个参数为数据库的包名
             Schema schema = new Schema(1, "com.alpha.db");
             // 创建表,参数为表名
             Entity entity = schema.addEntity("Info");
             // 为表添加字段
             entity.addIdProperty();// 该字段为id
             entity.addStringProperty("name");// String类型字段
             entity.addIntProperty("age");//Int类型字段
             entity.addStringProperty("tel");// String类型字段

             // 生成数据库相关类
             //第二个参数指定生成文件的本次存储路径,AndroidStudio工程指定到当前工程的java路径
             new DaoGenerator().generateAll(schema, "C:\\Users\\Alpha\\AndroidStudioProjects\\GreenDaoDemo\\app\\src\\main\\java");
         }
     }
     ```

  2. 在Application中通过DaoMaster.DevOpenHelper初始化数据库

     ```
     // 该初始化过程最好放在Application中进行,避免创建多个Session
     private void setupDatabase() {
         // 通过 DaoMaster 的内部类 DevOpenHelper创建数据库
         // 注意：默认的 DaoMaster.DevOpenHelper 会在数据库升级时，删除所有的表
         // 所以，在正式的项目中，你还应该做一层封装，来实现数据库的安全升级。
         /**
     ```

     - @param context :　Context
       - @param name : 数据库名字
       - @param factory : CursorFactroy
         */

     ```
         DaoMaster.DevOpenHelper helper = new DaoMaster.DevOpenHelper(this, "student.db", null);
         // 获取数据库
         SQLiteDatabase database = helper.getWritableDatabase();
         // 获取DaoMaster
         DaoMaster daoMaster = new DaoMaster(database);
         // 获取Session
         DaoSession daoSession = daoMaster.newSession();
         // 获取对应的表的DAO对象
         InfoDao dao = daoSession.getInfoDao();
     }
     ```

  3. 获取数据库的DAO对象,即可进行增删改查的操作

     ```
     // 增
     dao.insert(new Info(null, "zhangsan", 12, "13112345678"));
     // 删
     dao.deleteByKey(1L);
     // 改
     Info info = new Info(3L, "赵琦", 78, "18812348888");
     dao.update(info);
     // 查
     QueryBuilder<Info> builder = dao.queryBuilder();
     builder.where(InfoDao.Properties.Name.eq("lisi"));
     Query<Info> build = builder.build();
     List<Info> list = build.list();
     ```

### 

 






