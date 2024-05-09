<link rel="stylesheet" href="RDView.css">

<div class="RDView" style="--row:8; --column:15; --scale:0.75;">
	<div class="line"></div>
	<div class="event rooms" style="--event-width:1; --beat:0; --y:0; --event-x:0; --event-y:1;"><div class="condition-true"></div></div>
	<div class="beat" style="--tick:3; --beat:6; --y:0; --swing:0.25; --hold:1;">
		<div class="classybeat">
			<div></div>
			<div></div>
			<div></div>
			<div></div>
			<div></div>
			<div></div>
		</div>
		<div class="tag"></div>
		<div class="holdbeat"></div>
	</div>
	<div class="beat" style="--tick:1; --beat:6; --y:6; --interval:3; --delay:0.5;">
		<div class="freezeshot"></div>
		<div class="skipshot"></div>
	</div>
	<div class="beat" style="--tick:1; --beat:3; --y:4; --interval:2;">
		<div class="burnshot"></div>
	</div>
	<div class="beat" style="--tick:2; --beat:0; --y:6; --subdivision:2;">
		<div class="subdivision">
			<div></div>
		</div>
	</div>
	<div class="beat" style="--tick:3; --beat:1; --y:0;"></div>
	<div class="event rooms" style="--event-width:1; --event-height:4; --beat:1; --y:1; --event-x:2; --event-y:0;"></div>
	<div class="event sounds" style="--event-width:1; --event-height:1; --beat:4; --y:1; --event-x:3; --event-y:1;"></div>
	<div class="event actions" style="--event-width:1; --event-height:1; --beat:4; --y:2; --event-x:3; --event-y:0;"></div>
	<div class="beat" style="--tick:2; --beat:2; --y:3;"></div>
	<div class="event actions" style="--event-width:1; --event-height:1; --beat:1; --y:5; --event-x:5; --event-y:0;"></div>
	<div class="event sounds" style="--event-width:1; --event-height:1; --beat:4; --y:5; --event-x:1; --event-y:1;"></div>
	<div class="event sounds" style="--event-width:1; --event-height:1; --beat:4; --y:6; --event-x:9; --event-y:1;"></div>
	<div class="event decorations" style="--event-width:1; --event-height:1; --beat:7; --y:1; --event-x:9; --event-y:1;"></div>
	<div class="event actions" style="--event-width:1; --event-height:1; --beat:7; --y:2; --event-x:4; --event-y:1;"></div>
	<div class="event decorations" style="--event-width:1; --event-height:1; --beat:7; --y:3; --event-x:4; --event-y:0;"></div>
	<div class="event sounds" style="--event-width:1; --event-height:1; --beat:7; --y:4; --event-x:33; --event-y:1;"></div>
	<div class="event actions" style="--event-width:1; --event-height:1; --beat:7; --y:5; --event-x:19; --event-y:0;"></div>
	<div class="event decorations" style="--event-width:1; --event-height:1; --beat:10; --y:1; --event-x:39; --event-y:1;"></div>
	<div class="event actions" style="--event-width:1; --event-height:1; --beat:10; --y:2; --event-x:6; --event-y:1;"></div>
	<div class="event decorations" style="--event-width:1; --event-height:1; --beat:10; --y:3; --event-x:1; --event-y:1;"></div>
	<div class="event decorations" style="--event-width:1; --event-height:1; --beat:10; --y:4; --event-x:21; --event-y:1;"></div>
	<div class="event sounds" style="--event-width:1; --event-height:1; --beat:9; --y:5; --event-x:1; --event-y:0;"></div>
</div>

# RDView 参考文档

## 网格

默认为 4 行 8 列的网格。  

<div class="RDView"></div>

**超出网格的内容仍会被渲染。**

- `--row` 单元格行数。  
- `--column` 单元格列数。  

<div class="RDView" style="--row:3;--column:5;"><div class="event actions"></div><div class="event decorations" style="--beat:4;--y:2"></div></div>

- `--scale` 缩放。  

<div class="RDView" style="--scale:0.5"><div class="event actions"></div><div class="event decorations" style="--beat:7;--y:3"></div></div>

- `center` 居中。  

<div class="RDView center"><div class="event actions"></div><div class="event decorations" style="--beat:7;--y:3"></div></div>

- `transparent` 隐藏背景。  

<div class="RDView transparent"><div class="event actions"></div><div class="event decorations" style="--beat:7;--y:3"></div></div>

- `inline` （`<span>`）在行内显示。不支持节拍。  

链接到<a href="#"><span class="RDView inline" style="--row:1; --column:3; --scale:0.5;"><span class="event actions"></span><span class="event decorations" style="--beat:2"></span></span>本文档</a>。

## 节拍 `beat`
默认为 tick 为 1 的二拍子。

<div class="RDView" style="--row:2;--column:2;">
	<div class="beat"></div>
</div>

- `--beat` 列数/节拍数，0-base。  
- `--y` 行数，0-base。  
- `--hue` 事件的色调偏移。  
- `--brightness` 事件的亮度。
- `--grayscale` 事件的灰度。
- `--tick` 拍长。

<div class="RDView" style="--row:3;--column:4;">
	<div class="beat" style="--beat:1; --y:1; --tick:2;"></div>
</div>


- `freezeshot` 冰冻拍。
	- `--interval` 间隔。
	- `--delay` 延迟。
- `burnshot` 灼热拍。
	- `--interval` 间隔。
- `skipshot` 跳过拍。
- `subdivision` 细分拍。
	- `--subdivision` 细分个数。
		- 需要添加 (`--subdivision` - 1) 个 `<div>`。
- `classybeat` 七拍子。
	- 需要添加 6 个 `<div>`。
	- `--swing` 摇摆拍。
- `holdbeat` 长按拍。
	- `--hold` 长按。
- `condition-true` 条件-真。
- `condition-false` 条件-假。
- `condition-both` 条件-皆有。
- `tag` 标签。

<div class="RDView" style="--row:10;--column:8;">
	<div class="beat" style="--beat:1; --y:0; --tick:2; --interval:3; --delay: 0.5;">
		<div class="freezeshot"></div>
	</div>
	<div class="beat" style="--beat:1; --y:1; --tick:0.5; --interval:1.5;">
		<div class="burnshot"></div>
	</div>
	<div class="beat" style="--beat:1; --y:2; --tick:1;">
		<div class="skipshot"></div>
	</div>
	<div class="beat" style="--beat:1; --y:3; --tick:1; --subdivision:3;">
		<div class="subdivision">
			<div></div>
			<div></div>
		</div>
	</div>
	<div class="beat" style="--beat:1; --y:4; --tick:6; --swing:0.5;">
		<div class="classybeat">
			<div></div>
			<div></div>
			<div></div>
			<div></div>
			<div></div>
			<div></div>
		</div>
	</div>
	<div class="beat" style="--beat:1; --y:5; --tick:3; --hold:1.5;">
		<div class="classybeat">
			<div></div>
			<div></div>
			<div></div>
			<div></div>
			<div></div>
			<div></div>
		</div>
		<div class="holdbeat"></div>
	</div>
	<div class="beat" style="--beat:1; --y:6;">
		<div class="condition-true"></div>
	</div>
	<div class="beat" style="--beat:1; --y:7;">
		<div class="condition-false"></div>
	</div>
	<div class="beat" style="--beat:1; --y:8;">
		<div class="condition-both"></div>
	</div>
	<div class="beat" style="--beat:1; --y:9;">
		<div class="tag"></div>
	</div>
</div>

## 其他事件 `event`

- `sounds` 声音事件。  
对应图片文件 `/assets/events/sounds.png`。
- `actions` 动作事件。  
对应图片文件 `/assets/events/actions.png`。
- `decorations` 精灵事件。  
对应图片文件 `/assets/events/decorations.png`。
- `rooms` 房间事件。  
对应图片文件 `/assets/events/rooms.png`。

<div class="RDView" style="--row:5;--column:2;">
	<div class="event sounds"></div>
	<div class="event actions" style="--y:1;"></div>
	<div class="event decorations" style="--y:2;"></div>
	<div class="event rooms" style="--y:3;"></div>
</div>

- `--beat` 事件的节拍。
- `--y` 事件的高度。
- `--hue` 事件的色调偏移。
- `--brightness` 事件的亮度。
- `--grayscale` 事件的灰度。
- `--event-x` 截取对应图片文件中指定列的事件。
- `--event-y` 截取对应图片文件中指定行的事件。
- `--event-width` 截取事件的宽度。
- `--event-height` 截取事件的高度。

<div class="RDView" style="--row:8;--column:7;">
	<div class="event sounds" style="--beat:1; --y:1; --event-width:5; --event-x:10; --event-y:2;"></div>
	<div class="event rooms" style="--beat:1; --y:3; --event-height:4; --event-x:1;"></div>
</div>

- `condition-true` 条件-真。
- `condition-false` 条件-假。
- `condition-both` 条件-皆有。
- `tag` 标签。

<div class="RDView" style="--row:5;--column:2;">
	<div class="event sounds">
		<div class="condition-true"></div>
	</div>
	<div class="event actions" style="--y:1;">
		<div class="condition-false"></div>
	</div>
	<div class="event decorations" style="--y:2;">
		<div class="condition-both"></div>
	</div>
	<div class="event rooms" style="--y:3;">
		<div class="tag"></div>
	</div>
</div>

## 描述 `description`（存在问题）  
事件都可以添加描述框。  
鼠标悬浮在事件上以展示描述框内容。

<div class="RDView" style="--row:3;--column:3;">
	<div class="event sounds" style="--event-x:4;">
		<div class="description">在二拍子的起拍点添加护士语音事件“Set”。</div>
	</div>
	<div class="event sounds" style="--beat:1; --event-x:5;">
		<div class="description">在二拍子的落拍点添加护士语音事件“Go”。</div>
	</div>
	<div class="beat" style="--y:1;">
		<div class="description">此二拍子的拍长为 1 。</div>
	</div>
</div>

- `--line-count` 行数。  
- `text` 节奏医生风格的矢量文本。  
	- `left` 左对齐。
	- `center` 中心对齐。
	- `right` 右对齐。
- `box` 节奏医生风格的矢量文本框。  
	- `left` 左对齐。
	- `center` 中心对齐。
	- `right` 右对齐。

<div class="RDView" style="--row:2;--column:3;">
	<div class="event sounds" style="--event-width:2; --event-y:3;">
		<div class="description" style="--line-count:2;">
			<div class="text" style="--text-box-width:20;">BPM</div>
			<div class="box center" style="--text-box-width:50;">100</div>
		</div>
	</div>
</div>