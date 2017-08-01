## AlloyCrop 1.0 ����

[AlloyCrop](https://github.com/AlloyTeam/AlloyCrop) �����Ŀ��8����ǰ�����ģ���Ϊ[AlloyFinger](https://github.com/AlloyTeam/AlloyFinger) �ĵ��Ͱ���������֮��BAT��������˾�㷺ʹ�á����Ƿ���֮������������һֱû�г��ʱ��ȥ���:

* �ü�ͼ��ķֱ���̫С���Ƿ���䣿
* pinch˫ָ�Ŵ��ʱ�򣬷Ŵ�����Ĳ���˫ָ���ģ��Ƿ�����Ż���

���ںܸ��˵ظ��ߴ�ң�AlloyCrop �Ѿ���ȫ�㶨�������������⣬���Ľ������°汾�ı仯��AlloyCrop�����ԭ����ȻAlloyFinger��ԭ������Ͳ��ٲ�������ǰ�з���� [��СWeb���ƿ�AlloyFingerԭ��](./asset/alloyfinger.md)

�ȿ�ȫ�µ�API�仯��

## API

```js
new AlloyCrop({
    image_src: "img src",
    circle: true, // optional parameters , the default value is false
    width: 200, // crop width
    height: 100, // crop height
    output: 2, // output resolution --> 400*200
    ok: function (base64, canvas) { },
    cancel: function () { },
    ok_text: "yes", // optional parameters , the default value is ok
    cancel_text: "no" // optional parameters , the default value is cancel
});
```

���� |�Ƿ���� | ����
----|------|----
image_src | ����  | ��Ҫ�ü�ͼƬ��src��ַ
circle | �����룬Ĭ����false  | ����ѡȡ���Ƿ���Բ�λ��Ǿ��Σ�Ĭ���Ǿ��Σ�ע��:Բ��ѡȡ�ü�������Ҳ��������ͼƬ
width | ����  | ѡ���Ŀ�
height | ����  | ѡ���ĸ�
output | ���� | ����ı��ʡ��������outputΪ2��ѡ���Ŀ�300��ѡ���ĸ�100�������ͼ��ķֱ���Ϊ (2��300��2��100��
ok | ����  | ���ok��ť�Ļص�
cancel | ����  | ���cancel��ť�Ļص�
ok_text | �����룬Ĭ����ok  | ok��ť���ı�
cancel_text | �����룬Ĭ����cancel  | cancel��ť���ı�

��֮ǰ�汾����Ҫ�ı仯���������� output ֧���Զ��屶�ʷֱ��ʵ�ͼ�������

## outputԭ��

```js
crop: function () {
    this.calculateRect();
    this.ctx.drawImage(this.img, this.crop_rect[0], this.crop_rect[1], this.crop_rect[2], this.crop_rect[3], 0, 0, this.canvas.width, this.canvas.height);

},
```

���� this.calculateRect() �Ǽ���ѡȡ��ͼƬ�ص���һ��ľ�������drawImage �ǰѲü���������Ƶ� canvas �ϡ�ע�� canvas �Ŀ���Ƕ��٣��ҿ�:

```js
this.canvas.width = option.width * this.output;
this.canvas.height = option.height * this.output;
```

���Ծʹﵽ���Զ��屶�ʷֱ��ʵ�Ŀ�ġ���Ȼ����ͼƬ��ʧ���ֻ��߳��ֱ棬��ȡ���� drawImage ��ֵ���̡����ڲ�ֵ����ǰ����Աȹ���ʹ�����ξ����ֵ�걬����������,�������ξ����ֵ�ٶ�Ҳ������������������ں�ҪȨ��Ч�ʺͲ�ֵ���ȥʵ�� drawImage��

![img](http://images2017.cnblogs.com/blog/105416/201708/105416-20170801102838052-884320030.jpg)

## calculateRect����ü�����

��Ϊ������Ҫ��ͼƬ��ĳ��������Ƶ�����canvas�ϡ�����drawImage�ĺ��ĸ�����Ϊ��0, 0, this.canvas.width, this.canvas.height����Ȼ��������Ҫȥ����ͼƬ�ü�������

![pv](http://images2017.cnblogs.com/blog/105416/201708/105416-20170801103251646-2132149523.jpg)

��žͷ��������������һ������ȫ������һ�ֲ����ཻ��

![](http://images2017.cnblogs.com/blog/105416/201708/105416-20170801104639005-638761920.jpg)

![](http://images2017.cnblogs.com/blog/105416/201708/105416-20170801104749802-38131761.jpg)

��ΪͼƬ�ᱻ�Ŵ������С(scale)���������������΢����һ��㡣����ཻ�ľ��������Ҫ��ͼƬscale����У����У���ص�1�ı�������������drawImage���������μ� [https://github.com/AlloyTeam/AlloyCrop/blob/master/alloy-crop.js#L227-L255](https://github.com/AlloyTeam/AlloyCrop/blob/master/alloy-crop.js#L227-L255)

## pinch �����Ż�

ʹ��AlloyCrop�ǿ��ԷŴ������С�ٽ��вü�����ô���� pinch ��������ָ���м���зŴ��أ����Ե����ܶ������multipointStart�

*��multipointStart��AlloyFinger�׳��Ķ���ָ��ʼ������Ļ�Ļص�������ͨ��evt.touches�õ�ǰ������ָ������ȥ������������
* ���� originX �� originY��������ָ������
* ������ translateX �� translateY��ȥĨƽ��originX��originY���������λ��
	
```js
 new AlloyFinger(this.croppingBox, {
	multipointStart: function (evt) {
	    //reset origin x and y
	    var centerX = (evt.touches[0].pageX + evt.touches[1].pageX) / 2;
	    var centerY = (evt.touches[0].pageY + evt.touches[1].pageY) / 2;
	    var cr = self.img.getBoundingClientRect();
	    var img_centerX = cr.left + cr.width / 2;
	    var img_centerY = cr.top + cr.height / 2;
	    var offX = centerX - img_centerX;
	    var offY = centerY - img_centerY;
	    var preOriginX = self.img.originX
	    var preOriginY = self.img.originY
	    self.img.originX = offX / self.img.scaleX;
	    self.img.originY = offY / self.img.scaleY;
	    //reset translateX and translateY
	    self.img.translateX += offX - preOriginX * self.img.scaleX;
	    self.img.translateY += offY - preOriginY * self.img.scaleX;
	    self.initScale = self.img.scaleX;
	},
	pinch: function (evt) {
	    self.img.scaleX = self.img.scaleY = self.initScale * evt.zoom;
	},
	pressMove: function (evt) {
	    self.img.translateX += evt.deltaX;
	    self.img.translateY += evt.deltaY;
	    evt.preventDefault();
	}
});
```

	ע�⣬translateX, translateY, translateZ, scaleX, scaleY, scaleZ, rotateX, rotateY, rotateZ, skewX, skewY, originX, originY, originZ ���� [css3transform ���](https://alloyteam.github.io/AlloyTouch/transformjs/) ע�뵽DOMԪ���ϵ����ԡ�


## Preview

![Preview](http://images2017.cnblogs.com/blog/105416/201707/105416-20170731173956990-1895070647.jpg)

## Install

You can install it via npm:

```html
npm install alloycrop
```

Or get it from CDN:

[https://unpkg.com/alloycrop@1.0.1/alloy-crop.js](https://unpkg.com/alloycrop@1.0.1/alloy-crop.js)



## Demo

![./asset/alloycrop.png](./asset/alloycrop.png)

## Dependencies

* [AlloyFinger](https://github.com/AlloyTeam/AlloyFinger)
* [css3transform](https://alloyteam.github.io/AlloyTouch/transformjs/)


## License
This content is released under the [MIT](http://opensource.org/licenses/MIT) License.