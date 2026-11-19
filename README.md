基于深度学习YOLOV11传送带上煤炭煤矸石实例分割系统![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/94bfb4b987e54d5994200ba6a382414a.png)
  传送带上煤炭煤矸石实例分割数据集，2032张，yolo，voc，coco三种标注方式
数据集统计信息![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/315a6cc2e46249ec8ca3a079f32a8650.png)

====================
图像尺寸:312*312
类别数量: 2 类
训练集图像:1936; 验证集图像:79; 测试集图像:17
总图像数: 2032
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/1c2dbcfbe4db4e8d8d7614455f4e1c4b.png)

类别分布:
类别名称 | 包含该类别的图像数 | 总标注数
----------------------------------------![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/66d5a66b1b4d4008ad6d1871389cf415.png)

coal | 2027 | 25060
gangue | 1131 | 3546

模型代码：模型训练使用yolov11n-seg训练，80个epoch训练结果，map如描述图所示。![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/5a8c9365526b4861814231d6e550c177.png)

qt界面：运行界面采用pyqt5编写，本项目已经训练好模型，配置好环境后可直接使用，运行效果见描述图像![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/10342a0bbd0c4352a5b0c763d4297c5f.png)



# 传送带上煤炭煤矸石实例分割数据集

| 项目 | 详情 |
| --- | --- |
| 数据集名称 | 传送带上煤炭煤矸石实例分割数据集 |
| 总图像数量 | 2032张 |
| 图像尺寸 | 312*312 |
| 标注格式 | YOLO + VOC + COCO |
| 类别数量 | 2类 |
| 数据集划分 | 训练集：1936张   验证集：79张   测试集：17张 |

### 类别明细

| 类别 | 中文名称 | 含该类图像数 | 标注总数 |
| --- | --- | --- | --- |
| coal | 煤炭 | 2027 | 25060 |
| gangue | 煤矸石 | 1131 | 3546 |

### 配套说明

模型：YOLOv11n-seg，训练轮次80 epoch
界面：PyQt5推理界面，含训练权重，配置环境即可直接运行，支持图片/视频/摄像头推理，检测结果保存导出

### 应用价值

用于煤矿皮带输送场景，实现煤与矸石自动分割识别、体积占比统计、智能分选，是煤矸石智能分拣、煤矿自动化检测项目数据集。

```
# YOLOv11n-seg 训练脚本
from ultralytics import YOLO

if __name__ == '__main__':
    model = YOLO("yolov11n-seg.pt")
    model.train(
        data="coal_gangue.yaml",
        epochs=80,
        imgsz=312,
        batch=16,
        device=0
    )
```

```
# PyQt5 推理启动代码
import sys
from PyQt5.QtWidgets import QApplication
from seg_ui import MainWindow

if __name__ == '__main__':
    app = QApplication(sys.argv)
    window = MainWindow()
    window.show()
    sys.exit(app.exec_())
```


