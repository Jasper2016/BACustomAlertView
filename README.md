# BACustomAlertView
一个完全实现自定义的alertView！

> ##目前为止，最为精简的alert封装，以后alert就用博爱的[『BACustomAlertView』](https://github.com/boai/BACustomAlertView)了！


博爱的alert特点：
* 简单的两行搞定一个自定义alert
* 手势触摸隐藏
* 可以自定义背景图片、按钮颜色
* 可以添加文字和图片，且可以滑动查看
* 理论完全兼容目前所有 iOS 系统版本

####注：目前此版本只支持竖屏适配，小伙伴儿记得哦！


## 1、代码示例：
```
- (IBAction)buttonAction:(UIButton *)sender
{
    if (sender.tag == 1)
    {
        /*! 1、类似系统alert【加边缘手势消失】 */
        _alertView1 = [[BACustomAlertView alloc] ba_showTitle:@"博爱温馨提示："
                                                      message:titleMsg1
                                                        image:nil
                                                 buttonTitles:@[@"取消", @"确定"]];
        /*! 显示alert */
        [_alertView1 ba_showAlertView];
        
        BAWeak;
        _alertView1.buttonActionBlock = ^(NSInteger index){
            if (index == 0)
            {
                NSLog(@"点击了取消按钮！");
                /*! 隐藏alert */
                [weakSelf.alertView1 ba_dismissAlertView];
            }
            else if (index == 1)
            {
                NSLog(@"点击了确定按钮！");
                /*! 隐藏alert */
                [weakSelf.alertView1 ba_dismissAlertView];
            }
        };
    }
    else if (sender.tag == 2)
    {
        /*! 2、自定义按钮颜色 */
        _alertView2 = [[BACustomAlertView alloc] ba_showTitle:@"博爱温馨提示："
                                                      message:titleMsg2
                                                        image:nil
                                                 buttonTitles:@[@"取消", @"确定"]];
        /*! 自定义按钮文字颜色 */
        _alertView2.buttonTitleColor = [UIColor orangeColor];
        /*! 显示alert */
        [_alertView2 ba_showAlertView];
        BAWeak;
        _alertView2.buttonActionBlock = ^(NSInteger index){
            if (index == 0)
            {
                NSLog(@"点击了取消按钮！");
                /*! 隐藏alert */
                [weakSelf.alertView2 ba_dismissAlertView];
            }
            else if (index == 1)
            {
                NSLog(@"点击了确定按钮！");
                /*! 隐藏alert */
                [weakSelf.alertView2 ba_dismissAlertView];
            }
        };
    }
    else if (sender.tag == 3)
    {
        /*! 3、自定义背景图片 */
        _alertView3 = [[BACustomAlertView alloc] ba_showTitle:@"博爱温馨提示："
                                                      message:titleMsg1
                                                        image:nil
                                                 buttonTitles:@[@"取消", @"确定"]];
        /*! 自定义按钮文字颜色 */
        _alertView3.buttonTitleColor = [UIColor orangeColor];
        /*! 自定义alert的背景图片 */
        _alertView3.bgImageName = @"背景.jpg";
        /*! 显示alert */
        [_alertView3 ba_showAlertView];
        BAWeak;
        _alertView3.buttonActionBlock = ^(NSInteger index){
            if (index == 0)
            {
                NSLog(@"点击了取消按钮！");
                /*! 隐藏alert */
                [weakSelf.alertView3 ba_dismissAlertView];
            }
            else if (index == 1)
            {
                NSLog(@"点击了确定按钮！");
                /*! 隐藏alert */
                [weakSelf.alertView3 ba_dismissAlertView];
            }
        };
    }
    else if (sender.tag == 4)
    {
        /*! 4、内置图片和文字，可滑动查看 */
        _alertView4 = [[BACustomAlertView alloc] ba_showTitle:@"博爱温馨提示："
                                                      message:titleMsg1
                                                        image:[UIImage imageNamed:@"美女.jpg"]
                                                 buttonTitles:@[@"取消", @"确定"]];
        /*! 自定义按钮文字颜色 */
        _alertView4.buttonTitleColor = [UIColor orangeColor];
        /*! 自定义alert的背景图片 */
        _alertView4.bgImageName = @"背景.jpg";
        /*! 是否显示动画效果 */
        _alertView4.isShowAnimate = YES;
        /*! 显示alert */
        [_alertView4 ba_showAlertView];
        BAWeak;
        _alertView4.buttonActionBlock = ^(NSInteger index){
            if (index == 0)
            {
                NSLog(@"点击了取消按钮！");
                /*! 隐藏alert */
                [weakSelf.alertView4 ba_dismissAlertView];
            }
            else if (index == 1)
            {
                NSLog(@"点击了确定按钮！");
                /*! 隐藏alert */
                [weakSelf.alertView4 ba_dismissAlertView];
            }
        };
    }
    else if (sender.tag == 5)
    {
        /*! 5、完全自定义alert */
        UIView *view1 = [UIView new];
        view1.frame = CGRectMake(30, 100, SCREENWIDTH - 60, 200);
        view1.backgroundColor = [UIColor yellowColor];
        view1.layer.masksToBounds = YES;
        view1.layer.cornerRadius = 10.0f;
        //    view1.clipsToBounds = YES;
        
        _titleLabel = [UILabel new];
        _titleLabel.frame = CGRectMake(0, 0, view1.frame.size.width, 40);
        _titleLabel.text = @"测试title";
        _titleLabel.textAlignment = NSTextAlignmentCenter;
        _titleLabel.font = [UIFont systemFontOfSize:18];
        _titleLabel.backgroundColor = [UIColor greenColor];
        [view1 addSubview:_titleLabel];
        
        _chooseBtn = [[UIButton alloc]initWithFrame:CGRectMake(0, view1.frame.size.height - 40, view1.frame.size.width, 40)];
        [_chooseBtn setTitle:@"取消" forState:UIControlStateNormal];
        [_chooseBtn setBackgroundColor:[UIColor redColor]];
        [_chooseBtn setTitleColor:[UIColor whiteColor] forState:UIControlStateNormal];
        [_chooseBtn addTarget:self action:@selector(chooseBtnClick:) forControlEvents:UIControlEventTouchUpInside];
        [view1 addSubview:_chooseBtn];

        _alertView5 = [[BACustomAlertView alloc] initWithCustomViewiew:view1];
        [_alertView5 ba_showAlertView];
    }
}

- (void)chooseBtnClick:(UIButton *)sender
{
    NSLog(@"点击了取消按钮！");
    /*! 隐藏alert */
    [_alertView5 ba_dismissAlertView];
}

```
---

## 2、图片示例：
![image1](https://github.com/boai/BACustomAlertView/blob/master/image2.png)

![image2](https://github.com/boai/BACustomAlertView/blob/master/image.png)

---

## 3、个人简介
方式     | 链接 | 
:----------- | :-----------: | 
微博     | [『博爱1616』](http://weibo.com/2706728003/profile?rightmod=1&wvr=6&mod=personinfo&is_all=1)        |
博客     | [『http://boai.github.io』](http://boai.github.io)   | 
简书     | [『简书』](http://www.jianshu.com/users/95c9800fdf47/latest_articles) | 
简书专题  | [『简书专题链接』](http://www.jianshu.com/collection/072d578bf782) | 
QQ       | `137361770`        | 
iOS 10技术开发群       | `479663605`        | 

    为解决广大小白项目中遇到的各种疑难杂症，博爱新建了QQ群 `479663605`，希望广大小白和大神能够积极加入！

**~~老司机也欢迎！~~**

---

## 4、推荐
序号 | 类库 | 简介及功能介绍 
:----------- | :-----------: | :-----------
3.1         | [『BAButton』](https://github.com/boai/BAButton)        | 完全实现 UIButton 的自定义的类库。pod 导入：`pod 'BAButton', '~> 1.0.1'`
3.2         | [pod安装和使用方法](http://www.cnblogs.com/boai/p/4977976.html)        | 对pod还是不熟的同学，可以看下我的博客，是最新的pod安装和使用方法，一直更新！
3.3         | [『BASegmentControl』](https://github.com/boai/BASegmentControl)        | 新增网易新闻的滑动SegmentControl，基于[『HMSegmentedControl』](https://github.com/HeshamMegid/HMSegmentedControl)的完美二次封装！
3.4         | [『BAReminderDemo』](https://github.com/boai/BAReminderDemo)        | 系统提醒和日历提醒，最近做了一个预约功能，有用到系统提醒和日历提醒，就写了这个demo！
3.5         | [『BALocalNotification』](https://github.com/boai/BALocalNotification)        | 本地通知最新完美封装，最近整理了下本地通知和极光推送，有很多坑都踩过了，刚刚整理出来的完美封装，肯定适合大部分场合，也可以用此封装写闹钟，也提醒事件，都可以！如果喜欢，请在git上点个星吧！
3.6         | [『BANetManager』](https://github.com/boai/BANetManager)        | 基于[『AFNetworking 3.1』](https://github.com/AFNetworking/AFNetworking)！最新版本的封装，集成了get/post 方法请求数据，单图/多图上传，视频上传/下载，网络监测 等多种网络请求方式！
3.7         | [『APP中的文字和APP名字的国际化多语言处理』](http://www.cnblogs.com/boai/p/5337558.html)        | 最全、最贴心的国际化处理博客！
3.8         | 3D Touch的纯代码实现方法        | 详见：[『BABaseProject』](https://github.com/boai/BABaseProject)中的`appdelegate`！
3.9         | [『BACustomAlertView』](https://github.com/boai/BACustomAlertView)       | 目前为止，最为精简的alert封装，以后alert就用博爱的[『BACustomAlertView』](https://github.com/boai/BACustomAlertView)！


---

## 5、系统要求

    该项目最低支持 iOS 7.0 ，理论支持目前所有 iOS 系统版本！


---