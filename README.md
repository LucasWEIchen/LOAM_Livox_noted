# LOAM_LIVOX_noted

## A Noted code of LOAM_Livox based on [loam_livox](https://github.com/hku-mars/loam_livox) 

## 备注版 LOAM_Livox

### Orginal [LOAM](https://github.com/cuitaixiang/LOAM_NOTED)

### The author crashed me with his magnificent C++ skill and extraordinary spatial visualization ability, Ohh what a func!

#### 作者用大师般的C++创作技巧将我按在屏幕上反复摩擦：

        雷军：有人说我写的代码像诗一样优雅


Overall, the structure of LOAM_Livox is the same as the original LOAM. Coding wise, the code is revised according to A-LOAM.

The entry point is laser_feature_extractor. Then it called livox_feature_extractor in the laser callback. livox_feature_extractor contains functions which processing the unique scan pattern of Livox and divided it into lines which can be pushed into LOAM algorithms. The code should also support Velodyne LiDARs by changing some parameters. There are some modifications in laser_feature_extractor to interfacing Livox scan pattern. Large part of the code is for testing and illustrating and not related with the core process.

Featurer_extractor only dealing with point cloud filtering and selecting. Then all surface/plane points is piped to laser_mapping. The rest is quite the same as LOAM but in multi-thread.