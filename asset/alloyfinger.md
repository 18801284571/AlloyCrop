# ��СWeb���ƿ�AlloyFingerԭ��

Ŀǰ[AlloyFinger](https://github.com/AlloyTeam/AlloyFinger)��Ϊ��Ѷ�ֻ�QQ web���ƽ���������ڸ�����Ŀ�ж����������á�
����Ȥ��ͬѧ����ȥGithub������[https://github.com/AlloyTeam/AlloyFinger](https://github.com/AlloyTeam/AlloyFinger)

����Ѷ���磺��Ȥ���䡢QQȺ��QQ��������ѶѧԺ��TEDxTencent�� AlloyTeam����ѶCDC�ȶ�����š��ŶӺ���Ŀ����ʹ��AlloyFinger������ͼ��ʾ��

![](http://images2015.cnblogs.com/blog/105416/201611/105416-20161111095753405-852368951.png)


������ֻҪ��ͼ��ü���ͼ��鿴�ĵط�����ʹ�õ�AlloyFinger�����AlloyFingerҲ��ѡ����Ѷcodeƽ̨�ľ�Ʒ�����


![](http://images2015.cnblogs.com/blog/105416/201611/105416-20161111095828124-1504358796.png)



���˹��������Ŀ�ŶӶ���ʹ��AlloyFinger��������ĸ���IT��վҲ������ת�ر�������Ϊ����С�����ƿ⣬��Ѷ��web��ĿΪʲô��ѡ��hammerjs��ѡ��[AlloyFinger](https://github.com/AlloyTeam/AlloyFinger)?����Ӹ����Ƕȡ��ܹ���ԭ���Ͻ���һ�·�����

## ���

![](http://images2015.cnblogs.com/blog/105416/201611/105416-20161111095834749-1098555058.png)


���Կ���hammerjs���ԶԶ����AlloyFinger�������ֻ�QQ web�����ٶ�����׷���µ�ͬѧ��˵��ʹ��hammerjs�Ĵ�С�ǲ����Խ��ܵģ�
��ô��Ϊʲôhammerjs��ô�󣿿��¼ܹ���Ʊ��֪����

##�ܹ����

![](http://images2015.cnblogs.com/blog/105416/201611/105416-20161111095852327-1033161544.png)

![](http://images2015.cnblogs.com/blog/105416/201611/105416-20161111095857280-1590883491.png)


��ʵ��hammerjs�������Class��û���о�ȫ��������ࡣ���Թ��ȹ��̻�������������ر��
һ���õ���Ʋ�����Ҫ��ÿ���߼��㶼����������ֲ����̻�������OO�ǿ��ԡ���AlloyFinger����ơ�����ֻ��Vector2��AlloyFinger����touchstart��touchmove��touchend�ǿ���trigger����ص������¼��ģ��򵥡�ֱ�ӣ�hammerjs��֧�ֵ����ƣ�AlloyFinger����֧�֡�

## ����ʵ��
������֪���������¶���ĸ��¼��������ߣ�touchstart touchmove touchend touchcancel�������ĸ��¼��Ļص����������õ�TouchEvent��
TouchEvent:
touches����ǰλ����Ļ�ϵ�������ָ�������б�
targetTouches��λ�ڵ�ǰ DOM Ԫ���ϵ���ָ�������б�
changedTouches���漰��ǰ�¼�����ָ�������б�
TouchEvent������õ�������ָ�����꣬��ô�ɱ���Ծ���ô�����ˡ�

## Tap�㰴

![](http://images2015.cnblogs.com/blog/105416/201611/105416-20161111095906045-733957741.png)


�ƶ���click��300������ʱ��tap�ı�����ʵ����touchend������Ҫ�ж�touchstart���ֵ������touchendʱ���ֵ�����x��y����ƫ��ҪС��30��С��30�Ż�ȥ����tap��

## longTap����

![](http://images2015.cnblogs.com/blog/105416/201611/105416-20161111095918014-817827393.png)

touchstart����һ��750�����settimeout�����750ms����touchmove����touchend����������ö�ʱ��������750msû��touchmove����touchend�ͻᴥ��longTap

## swipe��

![](http://images2015.cnblogs.com/blog/105416/201611/105416-20161111095922889-1492134948.png)


������Ҫע�⣬��touchstart���ֵ������touchendʱ���ֵ�����x��y����ƫ��Ҫ����30���ж�swipe��С��30���ж�tap����ô�û������Ǵ��ϵ��£����Ǵ��µ��ϣ����ߴ����ҡ����ҵ��󻬶��أ����Ը������������жϵó�������Ĵ������£�
```js
_swipeDirection: function (x1, x2, y1, y2) {
        return Math.abs(x1 - x2) >= Math.abs(y1 - y2) ? (x1 - x2 > 0 ? 'Left' : 'Right') : (y1 - y2 > 0 ? 'Up' : 'Down')
}
```

## pinch��
���������ʹ��Ƶ�ʷǳ��ߵģ���ͼ��ü���ʱ��Ŵ������СͼƬ������Ҫpinch��

![](http://images2015.cnblogs.com/blog/105416/201611/105416-20161111095941233-1102331240.png)


����ͼ��ʾ������֮��ľ����ֵ��pinch��scale�����scale�������event�ϣ����û�������dom��transform��������Ԫ�ص�scale���ԡ�

##rotate��ת

![](http://images2015.cnblogs.com/blog/105416/201611/105416-20161111095946795-1685550144.png)


����ͼ��ʾ�������ڻ������������������״̬֮��ļнǦȡ�����������ô����ת�����أ���ô��Ҫʹ�ò�ˣ�Vector Cross����
����cross������������ж���ת�ķ���

![](http://images2015.cnblogs.com/blog/105416/201611/105416-20161111100002889-1355904474.png)


cross������ʵ����������Կ�������Ƶ���

![](http://images2015.cnblogs.com/blog/105416/201611/105416-20161111100020467-1719129808.png)


���ԣ����������ﾭ����cross������ת����������Ϊ������ʵҪ�����˾��൱�������

![](http://images2015.cnblogs.com/blog/105416/201611/105416-20161111100026124-2061653823.png)


# �ܽ�

��Ҫ��һЩ�¼�����ԭ���Ѿ������潲�⣬������multipointStart��doubleTap��singleTap��multipointEnd���Կ�Դ�룬����200�еĴ���Ӧ�ú�����������trigger�����¼���ͬʱ��touchStart��touchMove��touchEnd��touchCancelͬ��Ҳ���Լ�����
��ϸ��Vector2��AlloyFinger�������ȥGithub�ϲ��ģ�
[https://github.com/AlloyTeam/AlloyFinger](https://github.com/AlloyTeam/AlloyFinger)
�κ�������߽��黶ӭ��issue��
[https://github.com/AlloyTeam/AlloyFinger/issues](https://github.com/AlloyTeam/AlloyFinger/issues)