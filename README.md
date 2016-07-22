# 提取grafana中的图表

---

## 说明

可以利用`grafana`从`influxdb`中读取数据，然后绘制相应的图表。具体可以参考[influxdb+collectd+grafana搭建监控系统](https://www.zybuluo.com/adonia/note/443802)。

例如，如下是使用`grafana`绘制的系统剩余磁盘的变化趋势:

![grafana-graph.png-41.6kB][../image/grafana-graph.png]

## 提取图表

在`grafana`中提取图表的方法，参考[图表提取](https://www.zybuluo.com/adonia/note/443802#提取图片)。

按照`grafana`中的介绍，嵌入的iframe如下:

```
<iframe src="http://192.168.102.16:3000/dashboard-solo/db/new-dashboard?from=1469156289206&to=1469159832858&panelId=3" width="450" height="200" frameborder="0"></iframe>
```

> Note:

> * `192.168.102.16:3000`为`grafana`的访问地址

> * `new-dashboard`为`grafana`中的dashboard名称

> * `from`和`to`后跟的是时间戳

> * `panelId`指定的是需要提取的图表的标识，可以通过`Dashboard的查询接口---GET http://{ip}:{port}/api/dashboards/db/{dashboard_name}`中的`panels`列表获取

这样，就可以在页面上指定获取图表的开始时间和结束时间，将`iframe`嵌入到指定的页面元素中。