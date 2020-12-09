# IDEA有关笔记  

## 相关注解

### 可以发现，代码中使用的并不是一般的JDBCtmplate连接数据库，主要是直接使用mybatis+mysql/redis，所以相关的注解有必要解释一下，免得以后看不懂。 

#### JPA相关注解  

* @entity：表明这是一个实体类，其中可以带有表示数据库的相关。
* @data：主要是为了简化JPA相关的代码
* @table：其中代码中主要使用的是name这个属性，主要作用是申明使用的数据库的名称，设置一般都在common-base里。
* @column：主要是定义了将成员属性映射到关系表中的哪一列和该列的结构信息
* transient：主要是表明那些属性是需要被序列化的。

## 相关数据库的结构都在common-base里表明，但是实现的思路是：定义与common-base中是所有的表结构，其余的模块使用，通过mybatis，映射到resource的mapper实现，然后通过sql语句对mysql进行操作，注意其中select的select属性对应着接口中的相关函数定义 

## 在controller中，一般使用的主要就是resultInfo，表现于common-base中，*entity表现于common-base。  此处，基本上表格对应一个  

## airspace-manager-server和attachment-manager-server，process-manager-server，user-manager-server使用的都是db_uavsystem，info-manager-server使用的是db_uavsystem_infomanager，也就是说附件使用的是额外的表格。分布式使用的是tx-manager，所以基本上使用到的MySQL数据库只有三个

## common-base里几个对于数据表格有操作的：airspace:TairspaceCircular(t_airspce_circular),TairspaceInfo(t_airspace_info),TAirspaceLine(t_airspace_line),TAirspaceLines(t_airspace_lines),TAirspacePolygon(t_airspace_polygon),TAirspacePolygons(t_airspace_polygons).infomanager:LicenseType(t_license_type),Tdevice(t_device),TFlyerInfo(t_flyer_info),TLicense(t_license),TuavInfo(t_uav_info).process:TairspacePlan(t_airspace_plan),TAirTraffic(t_air_traffic),TProcessInst(t_task_instance)。Certificates(t_certificates),CompanyType(t_CompanyType),UserAuthentication(t_user_authentication),UserEntity(t_user)

## tx-manager包含三个： hibernate_sequence，t_logger，t_tx_exception

## db_uavsystem包含19个：t_air_traffic ，t_airspace_circular， t_airspace_info，t_airspace_line，t_airspace_lines，t_airspace_plan ，t_airspace_polygon，t_airspace_polygons，t_certificates，t_companytype，t_department，t_inst_attachment ，t_kml_tracks，t_kml_tracks_copy1，t_process_task，t_role，t_role_resource，t_task_instance，t_user  

## db_uavsystem_infomanager包含五个：| t_device，t_flyer_info，t_license，t_license_type，t_uav_info  

## 好像找不到  tx-logger这个数据库  

## 