# WorldPopulationMap
使用pygal制作世界人口地图项目
1.从[开放数据源网站](#https://datahub.io)下载最新的世界人口信息。    
- 在search框里输入“population”
- 找到数据源之后下载json格式（linux系统下是右键另存为json）    
2.数据处理。    
```python
import json
with open("population_data.json")as f:
  data=json.load(f)
 ```
- 只需要“国别码”，”人口数“
- 通过country_code.py将数据中的国家名称转化为pygal可以识别的二位国别码。    
3.使用pygal内置的world map绘图。    
```python
import pygal
world_map_chart=pygal.map.world.World()
world_map_chart.title=""#设定标题
world_map_chart.add(数据名称，数据字典)#一个add为一组数据，可以多次add
world_map_chart.render_to_file(文件名)#将世界地图输出为svg文件，svg文件用浏览器打开
```
