# Web����

### �鼶Ԫ�أ����Դ���κζ�����С����

```html
<div>������</div> 
```



<html>       <!--�����������������һ��html�ļ�-->

```html
<head>       <!..ͷ����ǣ�����ĵ�������Ϣ�����ɼ�Ԫ��-->
<meta charset=''utf-8/''>       <!--�����ַ����룬��ֹ����-->
<title>wyword</title>      <!--�����ǩ��ָ����ҳ�ı���-->
<style tyle=''css/text''>
body{background-color}
h1{color:#fff;
text-align:center;
font-size:16px;
color:red;
}
</style>
</head>
```

<body>
<!--�������ݣ������ĵ��ɼ�����-->

<em>��ǩ���б������</em>
<br/>ǿ�ƻ���
<strong>�����ּӴ�</strong>
&nbsp;   ��ʾһ���ո�
<ins>��ʾ����»���</ins>
<del>���ɾ����</del>

```html
<p>�鼶Ԫ�أ�p��ǩ����ռһ�У�����������ǩ������ʾ
��������Ԫ�ؿ��Բ�����ʾ
�鼶Ԫ��װ���࣬���಻��װ�鼶Ԫ��
������ռ��width="55%"
���ߴ�ϸ size="4"
align="center" ���ݾ���  right ���ݾ���    left ͼƬ����
ͼƬ��Ⱥ͸߶��޸Ĵ���   width="ͼƬ���"   height="ͼƬ�߶�"
ͼƬ�������ҵľ����޸Ĵ���  hspace="ͼƬ���Ҿ���"
ͼƬ���¾����޸Ĵ��� vspace="ͼƬ���¾���"
ͼƬ����Ч��<p align="center"><img src="ͼƬ����"/</p>
ͼƬ��ӱ߿� border="�߿��ϸ"
src�����·�������ַ�����
```

### ����ͼƬ����ҳ�ļ���ʼ����

1�����·��

aͬ����  .html�ļ���ͼƬ��ͬһ���ļ�����
��ʽ  <img src="����ͼƬ��"/>

b�¼���   .html�ļ�����ͼƬ���ļ�����ͬһ���ļ�����
<img src="����ļ����Լ��ļ�����"

c�ϼ���  <img src="../�ļ�����"  ../��ʾ������һ��

����·��  <img src="�ļ�·��"
һ�㲻��ʹ��

�����ӣ�������ҳ��ת
a��ǩΪ������
�﷨��

```html
<a href="��ת��Ŀ�ĵ�ַ">��ʾ����</a>
```

ͼƬ������
�﷨��

```html
<a href="��ת��ַ"><img src="ͼƬ��ַ"></a>
```

���䳬����:

```html
<a href="mailto:�����ַ">��ʾ����</a>
```

�ļ����س����ӣ�

```html
<a href="�ļ�����">��ʾ����</a>
```

�ļ���׺����ΪͼƬ��׺��

<target="_blank"> �����Ӵ�һ���µ���ҳ��������ԭ����ҳ
<targer="_self"> ����ԭ����ҳ����ʾ�µ�ҳ�档

�����ӣ�<a href="#"> ��ʾһ��������

������ӣ������ӵ�һ�֣�����ͬһ����ҳ�ڽ�����ת��

```html
�﷨��<a href="#Ŀ�ĵ�ַ��id��"></a>
���磺<a href="#dibu">�ײ�</a>
```



          <h4 id="dibu">�ײ�</h4>

�����ӵ����ã���ת����ҳ���



### ���

���table
�У�tr
��Ԫ�� ��td
��ͷ�� ÿһ�е�����th 
���ı���Ϊ��<caption></caption>
���ı߿�Ϊ��border="�߿��ϸ"
���߿���ɫ��bordercolor="��ɫ"
�����û�и߶ȺͿ�ȣ������ɵ�Ԫ������ݴ�С
����Ԫ���п�Ⱥ͸߶ȣ�����û�ж��л��������ض��ĸ߶ȺͿ�ȣ��к��оͻ�ƽ�ֱ��Ŀ�Ⱥ͸߶�
���뷽ʽ�� table  align="left\center\right"
���ж��룺valign="top" top�϶���  middle���ж��� bottom�¶���   baseline ���߶���

```html
�߾ࣺcellspacing="��Ԫ��֮��ļ��"
��䣺cellpadding="���ݵ���Ԫ��߿�ļ��"
��Ԫ�񱳾���ɫ��bgcolor="��ɫ"
�кϲ���colspan="����" 
�кϲ���rowspan="����"
```




                                                        �б�

���ã�����ҳ�沼����ҳ�濴�������������
���ࣺ�����б�ʹ����ࣩ�������б�ʹ�ý��٣����Զ����б�
��1�������б�<ul></ul> 
                  �б���<li></li>
�﷨��

```html
<ul>
<li>�б�����</li>
<li>�б�����</li>
</ul>
```

��2���������б� <ol></ol>
�﷨��<ol>
<li>�б�����</li>
<li>�б�����</li>
<li>�б�����</li>
</ol>

type="disc" disc ʵ��Բ circle ����Բ square ʵ�ķ��� none �����б����

��3�����Զ����б�����������ݣ�������ĳ��������н���˵����<dl></dl>
���͵����ʣ�<dt></dt>
�������ʵ��<dd></dd>
�﷨��

<dl>
<dt>Ҫ���͵�����</dt>
<dd>����</dd>
<dd>����</dd>
<dd>����</dd>
</dl>
��ͷ����ǩ��ӿ������б�������߿�û�б߾�

```css
<style type="text/css">
*{
padding:0;
margin:0;
}
</style>
```

### �б�Ƕ��

```html
<h3>�б�Ƕ��</h3>
<h3>�ֻ����а�</h3>
<ul>
<li>��Ϊ</li>
<li>С��</li>
<li>ƻ��</li>
<li>����</li>
</ul>
```





�����û����̨���н�����ҳ�棺<form></form>
���ؼ���input�ؼ�������ǩ����ͨ����type�������ã�ָ���ؼ��Ĺ��ܡ�
�﷨

</form>

```css
textarea  �ı��� һ������װ�������Ķ���ı�
��ֹ��ק�ı��� ��resize : none
type="text"    �ǵ����ı���
type="password"    �����
type="submit"   �ύ��ť
onclick="alert('����ɹ�')"   ����ύ��ť��������Ϣ��
type="reset"    ���ð�ť
type="file"    �ϴ��ļ� Ĭ���ϴ�һ���ļ�        multiple="multiple"   �ϴ�����ļ�
<input type="image" src="img/13.png">ͼƬ��ǩ
```

### ����   from

```html
<form action="��������ַ" method="get/post">
<input type=""value=""name=""/>
</form>
```

get:�ύ�����ݻḽ����ַ���棬����ȫ
post:�Ὣ���ݴ�������������Ⱥ�������Ķ�ȡ

```css
autocomplete="off" / ָ�����Ƿ��Զ�������빦�ܡ�
size="����" �ı���ɼ��ַ�����
maxlength="����"  ����������������ַ�����
required="required"  �������ݲ���Ϊ��
type=""radio" ��ѡ��ť
checked="checked"  Ĭ��ѡ��״̬
type="checkbox"   ��ѡ��
placeholder="��������ȷ�������ַ"  ��ʾ��Ϣ����Ҫ�ֶ�ɾ��
autofocus="autofocus"    ����ҳ�Զ���ȡ���
```


label��ǩ�����ı��Ϳؼ���
�﷨��
<label for="�ؼ�id��">��</label>



### ������ʽ

ƥ������^��β$ \d=[0-9]�����ַ�\w(Ӣ����ĸ�������Լ��»���)

3λ���֣�^[0-9]{3}$=^\d{3}$

�����˵�<select></select>
�﷨��<select>
<option>	</option>
	</select>
datalist ��ǩ������ѡ���б�ͨ����input��ǩ���ʹ��
�﷨��
<input type="text" placeholder="������ϲ��������" list="mx">

<datalist id="mx">
<option>���»�</option>
<option>�����</option>
<option>���찮</option>
</datalist>
�����ı���

```html
<textarea rows="����" cols="����">
�����ı�
</textarea>
```

### padding :�ڱ߾�

����ʽ�����÷�Χ�ڱ���ǩ����
��Ƕʽ:   ������ȫ�ַ�Χ����


                                                                   �����

��ͬһ��������ͬһ�����������˶�����ԣ�ȥ����Ǹ���ʽ���ͽ�ԭ�򣩶�ͬһ������Ķ���������ö����ʽ�Ҳ���ͻ���Ե��ӡ�
				


ѡ����������ѡ�����͸���ѡ����
����ѡ���������ɵ���ѡ�������
��ǩѡ��������ѡ������idѡ������ͨ���ѡ������

��ǩѡ��������html�ı�ǩ��Ϊѡ����
�﷨����ǩ��{css��ʽ}
�����ʽ������ҳ�����һ���ǩ����Ч����ȱ�㲻�ܸ��Ի������ʽ��

��ѡ����:����ѡ��һ���򼸸�Ԫ����������ʽ
�﷨��.����{css��ʽ}����

<��ǩ�� class="����">***<��ǩ��>����ʽ�ĵ���
��ʽ�㶨�壺�ṹ��{class}���ã�һ������

idѡ������ѡ��Ψһ�ı�ǩ����������ʽ
�﷨��������ʽ
	#id��{��ʽ}
	������ʽ
	<p id="id��">****</p>

ͨ���ѡ������ѡ��ҳ�������еĶ���
�﷨��*{��ʽ}

����ѡ�������ɶ������ѡ������ɣ���Ϊ�˸���ȷ��ѡ��ĳ������
�﷨�� .����.���{��ʽ}��ʽֻ�Ժ��������
��ѡ������ѡ�񸸼��е����һ��
�﷨������>�Ӽ�{��ʽ}

����ѡ�������Զ������������ͬ����ʽ
�﷨����ǩ1����ǩ2����ǩ3{��ʽ}

α��ѡ���������ڶ�ĳЩѡ������������Ч��
����α��ѡ������
a:link(ѡ������û�б����ʵ�����)
a:visited(ѡ�������Ѿ������ʵ�����)
a��hover(ѡ�񾭹�������)
a:active(ѡ�񼤻�״̬������)

����ѡ����     a �� a:hover
Ԫ�ص���ʾģʽ
��Ԫ�أ���ռһ�У�div  h1-h6 p ul  li ol��
����Ԫ�أ�������ʾ��span strong a ��

�鼶Ԫ�ص��ص㣺��ռһ�� ���������ÿ��
display block ������Ԫ��ת��Ϊ�鼶Ԫ��



### ������ʽ

```css
font-size:�����С;
font-family(����): "����"," ����"   �пո��Ӣ����Ҫ�������
��������ʱ�����ʹ��Unicode���룬������Ч�ķ�ֹ�������ͬ�����µ�����
font-weight:(�����ϸ);   norma(Ĭ������)   bold�����壩bolder�����֣�
font-style(������);     normall(Ĭ�Ϸ��)  italic(б��)
�����ʽ���Բ�����ʾ������˳�����������������û��Ч����
text-decoration:none
white-space{�հ׷�����}�� normal{Ĭ��ֵ}�� nowrap{ǿ�Ʋ�����} pre{������ʽ��ʾ}	

overflow:���������ʾ��ʽ   visible�����ü���Ĭ�ϣ� hidden(�ü��������)         scroll(������ʾ)      auto�����������Զ�ѡ����ʾЧ����
text-overflow(�����ı���ʾ��ʽ)  clip(����ʾʡ�Ժ�)   ellipsis������������ʾʡ�Ժţ�
```

### ���ֹ���Ч��

```html
<marquee  align="left" behavior="scroll" bgcolor="#FF0000" direction="up" height="300" width="200" hspace="50" vspace="20" loop="1" scrollamount="100" scrolldelay="100" onMouseOut="this.start()" onMouseOver="this.stop()">hello worid!</marquee>
```

```css
text-indent(��������)  12px/2em/150%
text-decoration(�ı�����)��
none(Ĭ��û��������)
underline(���ı�����»���)
line-through:���ı����ɾ����
line-height  (�и�)=heightʱ���ݻᴹֱ����
```

```css
background-color��(������ɫ)/rgb(200,130,255);
background-color:transparent(Ĭ��͸��)
background-image: url(img/14.jpg); ���ñ���ͼƬ
background-size: cover;���ñ�����С cover ȫ������
������͸��ģʽ��rgba()
background-color:bgba(r,g,b,a(0-1)) aΪ͸����Ч��
opacity:���κζ��󶼿�������͸��Ч��
opacity��0-1
background-repeat:no-repeat/tepeat-x/tepeat-y
����ͼ��λ�ã�
background-positlon:left/center/right   top/center/bottom; ��/��/��
����ͼ��̶���
background-attachment: scroll;     scroll/ffxed
background-color image repeat attachment position ���Բ���˳��
����ģ��
1��������������ڱ߾࣬�ڱ߿� �߿���߾�
2���߿򣺴�ϸ����ʽ����ɫ
border��2px/solid(ʵ��) double(˫ʵ��) dashed(����) dotted(��ʵ��)/red
3���ڱ߾ࣺpadding.�����ݵ��߾�ľ���
padding:20px  ���������ڱ߾඼��20px
padding:10px 20px  ����Ϊ10px  ����Ϊ20px
padding:5px 10px 15px 20px ��5px ��10px ��15px ��20px 
4����߾ࣨmargin��:Ԫ����Ԫ��֮��
margin:10px  ��߾඼Ϊ10px
��߾�ϲ�ʱ��ȡ�ϴ��ֵ����������߾����
������Ƕ����һ������ʱ��ͬʱ������߾�������߾����ݣ����ԶԸ�Ԫ�ؼӱ߿�
margin��0px auto���Ժ�������ˮƽ���� ֻ�Կ鼶Ԫ����Ч
```



### ���ӵĸ���Ч��

��������float��
�﷨��ѡ����{float:left/center/right/none}
������Ӱ�����ı�׼��������Ҫȡ������
�﷨��
ѡ����{cleat:left/right/both(����):}
����һ��Ϊ������Ԫ�����һ���ֵ�Ϊ��Ԫ�أ��������Ԫ�ص���ʽΪcleat:left/right/both;
���������Ը���Ԫ�صĸ����Ӽ�overflow:hidden;��ʽ
Բ�Ǳ߿�border-redius��
�﷨��ѡ����{border-radius:1-4logth(ˮƽ�뾶)|%/1-4logth|%(��ֱ�뾶)}
��Բ������һ�������Σ�������Բ��border-radius���߳���һ��
���������Ұ�Բ������һ�������Σ����������Ұ�Բ��һ��

### Ԫ�صĶ�λ

��λ����ɣ���λģʽ�ͱ�ƫ��
��λģʽ����̬��static��/��Զ�λ��relative��/���Զ�λ��absolute��/�̶���fixed��; 

**�Ӿ�����**

```css
"ѡ����"{
	position:absolute;
    top:20px;
    right:30px;
}
```

### �̶���λ��fixed��

�����������Ϊ���յ㣬����Ԫ��û�й�ϵ�����������������

                                                                           ����ͼ
��Ҫ�����ú��ӵĿ�͸ߣ��ұߵ�����Ϊ�����·��ĺ���Ϊ��
background-position  ʹ��X���Y����ʵ�ֶ�λ

### ���������ʽ

�����ʽ�� cursor��pointer/С��  text/�ı�  move/�ƶ�  not-allowed/��ֹ

### ��λ�Ĳ㼶���� z-index

 z-index�����֣�����Խ�󣬲��Խ��

```css
���뷽ʽ
vertical-align :Ԫ�صĶ��뷽ʽ��ֻ�������Ԫ�ػ����ڿ鼶Ԫ����Ч���Կ鼶Ԫ����Ч
vertical-align��middle ��ʾ��ֱ���� /bottom ��ʾ���߶��� / top ��ʾ��������
```

### ����ԭ���Ķ��뷽ʽ

�ñ�ǩװ��ͼƬʱ����ʱ�ײ�����һЩ��࣬������Ϊ���ڿ鼶Ԫ��Ĭ�������ֻ��߶��룬����ͨ������ķ������

```css
1:��ͼƬ��� vertical-align:middle /top/bottom 
2:��ͼƬת��Ϊ�鼶Ԫ�� display :black
```

### ������������ʡ�Ժŵ���ʽ����

```css
overflow: hidden;      �����Ĳ���ʡ��
white-space: nowrap;     ǿ�Ʋ�����
text-overflow: ellipsis;    �����Ĳ�����ʡ�Ժŵ���ʽ����
```

?                                                     

������������ģ����ʾ
display:-webkit-box;
/*������һ����Ԫ����ʾ���ı�������*/
-webkit-line-clamp: 2;                   2��ʾ���ڶ�������ʾʡ�Ժ�
/*���û���������ж������Ԫ�ص����з�ʽ*/
-webkit-box-orient: vertical;

                                                         �������е����ȼ�

�������û�ж�λ������꾭��ʱ�����Զ�λ���ɣ�������ж�λ������Ҫ�������ȼ� z-index

### ��������Ϊ������

�������������Σ�����Ҫ�����ӿ�ߣ�border��10px soild  trasparent;  �Ѻ�����Ϊ͸��
��Ҫ�ı���ʾ�����ξ͸��ı����� border-����-��ɫ����ɫ��

```css
���Ӳ���Ҫ����ߣ��߿��ж�֣������ξ��ж��
	width:0;
	height:0;
	border-bottom: 50px solid pink;
	border-right: 50px solid blue;
	border-top: 50px solid red;
	border-left: 50px solid green;
ֱ�����������ô���
	width:0;
	height:0;
	border-bottom: 0px solid pink;
	border-right: 50px solid blue;
	border-top: 100px solid transparent;
	border-left: 0px solid green;
Ҳ����д�ɣ�
	width:0;
	height:0;
	border-color:transparent pink transparent transparent;
	border-style: solid;
	border-width: 100px 50px 0 0;
```

visibility:inherit �̳и������Ŀɼ��� /visible ������� /hidden ��������

```html
<div style="background: #000;height:127px;width:209px;top:0px;left:0px;"></div>
```

```css
style="display: none;background:rgba(0,0,0,0.6);height:127px;width:209px;top:0px;left:0px;"><div style="height:44px;width:46px;background:url(img/index.png) -189px -62px;margin-top:45px;margin-left: 80px;"
```



### ��������

�������������������˽��ǰ׺

```css
background: -webkit-linear-gradient(��λtop/bottom/left/right�� ��ʼ��ɫ����ɫ1����ɫ2��������);
```

### ���ַ�������Ϊ����

split(" ") ������������ʲô��Ϊ�ָ�� �� �� ���� 

```javascript

```

### ���ַ���ת��Ϊ��д  toUpperCase()

### ��������� ����ʾѡ��Ч��

input{outline:none}
