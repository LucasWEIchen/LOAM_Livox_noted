# LOAM_LIVOX_noted

## A Noted code of LOAM_Livox based on [loam_livox](https://github.com/hku-mars/loam_livox) 

## 备注版 LOAM_Livox
看完代码有一个疑问:/aft_mapped_to_init_high_frec 注意这个对应着原版LOAM中的高频帧间里程计实际上并没有被程序调用。 对应着laserOdometryHandler这个函数也根本没有执行, 也就没有发布高频里程计. 实际上LiVOX这个版本的LOAM中就没有使用帧间匹配,是不是因为激光没有重复扫描区域,所以加上帧间匹配效果适得其反. 如果去看大疆自己的git里面的官方简易版livox_loam,似乎也省略了帧间匹配,只保留了全图匹配. 这里先做记录再深入学习.

### Orginal [LOAM](https://github.com/cuitaixiang/LOAM_NOTED)

### The author crashed me with his magnificent C++ skill and extraordinary spatial visualization ability, Ohh what a func!

#### 作者用大师般的C++创作技巧将我按在屏幕上反复摩擦：

        雷军：有人说我写的代码像诗一样优雅


Overall, the structure of LOAM_Livox is the same as the original LOAM. Coding wise, the code is revised according to A-LOAM.

The entry point is laser_feature_extractor. Then it called livox_feature_extractor in the laser callback. livox_feature_extractor contains functions which processing the unique scan pattern of Livox and divided it into lines which can be pushed into LOAM algorithms. The code should also support Velodyne LiDARs by changing some parameters. There are some modifications in laser_feature_extractor to interfacing Livox scan pattern. Large part of the code is for testing and illustrating and not related with the core process.

Featurer_extractor only dealing with point cloud filtering and selecting. Then all surface/plane points is piped to laser_mapping. The rest is quite the same as LOAM but in multi-thread.