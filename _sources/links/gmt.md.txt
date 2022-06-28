# GMT

## Download Link

- [Official links](https://www.generic-mapping-tools.org/documentation/)
- Mirrors
    - [USTC mirror](https://mirrors.ustc.edu.cn/gmt/): 中国科学技术大学开源镜像
    - [NJU mirror](https://mirrors.nju.edu.cn/gmt/): 南京大学开源镜像

## Installation

- [GMT install guide](https://github.com/GenericMappingTools/gmt/blob/master/INSTALL.md)
- [GMT中文手册：安装](https://docs.gmt-china.org/latest/install/)

## Manuals & Tutorials

- [Official manual](https://docs.generic-mapping-tools.org/latest/index.html)
- [GMT 中文手册](https://docs.gmt-china.org/latest/)
- [GMT 教學手冊](https://gmt-tutorials.org/gallery.html)
- [GMT5 教程](https://jimmytseng79.github.io/GMT5_tutorials/) by Po-Chin Tseng

## CPT Libraries

- [Built-in color palette tables](https://docs.generic-mapping-tools.org/latest/cookbook/cpts.html?highlight=color)
    - [内置CPT in GMT中文手册](https://docs.gmt-china.org/latest/cpt/builtin-cpt/)
- [cpt-city](http://soliton.vm.bytemark.co.uk/pub/cpt-city/): An archive of colour gradients
- [cpt-city color tables](http://docs.idldev.com/vis/color/cptcity_catalog.html): API documentation for visualization library
    ```{note}
    Merge directory path and sub-path of cpt to download file

        wget http://docs.idldev.com/vis/color/cpt-city/cb/div/xxx.cpt

    ```
- [Scientific colour maps](https://www.fabiocrameri.ch/colourmaps/)
- [制作CPT](https://docs.gmt-china.org/latest/cpt/makecpt/)
    - Small square for NaN color
    - Cyclic CPT
    - Dynamic CPT

## Gallery

- [Built-in example gallery](https://docs.generic-mapping-tools.org/latest/gallery.html)
- [Built-in Animations](https://docs.generic-mapping-tools.org/latest/animations.html)
- [PyGMT gallery](https://www.pygmt.org/dev/gallery/index.html)
- [GMT中文手册：绘图实例](https://docs.gmt-china.org/latest/examples/)
- [GMT 教學手冊：章節地圖索引](https://gmt-tutorials.org/gallery.html)
- [GMT中文社区图库](https://gmt-china.org/gallery/) (no longer maintained)


## Geographic Dataset

### Global dataset
- [gshhg](http://www.soest.hawaii.edu/wessel/gshhg/): Global Self-consistent Hierarchical High-resolution Geography
    - [Readme of gshhg-gmt](https://github.com/GenericMappingTools/gshhg-gmt#readme)
    - [GSHHG: 全球高分辨率海岸线数据](https://docs.gmt-china.org/latest/dataset/gshhg/)

- [DCW-GMT](http://www.soest.hawaii.edu/wessel/dcw/): The Digital Chart of the World for GMT 6 or later
    - [Readme of DCW](https://github.com/GenericMappingTools/dcw-gmt#readme)
    - [DCW: 世界数字图表](https://docs.gmt-china.org/latest/dataset/dcw/)

- [Remote dataset](https://docs.generic-mapping-tools.org/latest/datasets/remote-data.html)
    - [GMT 远程数据](https://docs.gmt-china.org/latest/dataset/#id2)

- [PB2002](http://peterbird.name/publications/2003_PB2002/2003_PB2002.htm): A global set of present plate boundaries on the Earth is presented in digital form
    ```{admonition} Citation
    :class: seealso
    Bird, P. (2003) An updated digital model of plate boundaries, Geochemistry Geophysics Geosystems, 4(3), 1027, doi:10.1029/2001GC000252.
    ```
    - [PB2002: 全球板块边界数据](https://docs.gmt-china.org/latest/dataset/PB2002/)

- [World Geologic Maps](https://certmapper.cr.usgs.gov/data/apps/world-maps/): Collection of geologic maps
  - [Asia Pacific Region](https://pubs.er.usgs.gov/publication/ofr97470F)
  - [South Asia](https://pubs.er.usgs.gov/publication/ofr97470C)
  - [geo3al: 中国及邻区地质图数据](https://docs.gmt-china.org/6.2/dataset-CN/geo3al/)


### Chinese dataset

- [中国地理空间数据集](https://docs.gmt-china.org/latest/dataset-CN/)


### Unformatted dataset

- [全国地震活动断层分布图](https://activefault-datacenter.cn/faultzone/faultzone.html)
- [全国活动断层展示系统](http://www.neotectonics.cn/arcgis/apps/webappviewer/index.html?id=3c0d8234c1dc43eaa0bec3ea03bb00bc)