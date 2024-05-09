<style>
	div.RDEditor {
		width: calc(var(--scale) * 352px);
		height: calc(var(--scale) * 198px);
		background-color: black;

		&>div {
			position: absolute;
		}
	}

	.RDView {
		width: calc(var(--column, 8) * var(--scale, 1) * 28px);
		height: calc(var(--row, 4) * var(--scale, 1) * 28px);
		image-rendering: pixelated;		
		background-image: url(./assets/grid.png);
		background-size: calc(var(--scale, 1) * 28px);

		&.center{
            display: table;
            margin: 0 auto;
		}

		&.transparent{
			background-image: none;
		}

		&.inline{
			display: inline-block;
		}

		&>.event,
		>.beat,
		>.pulse {
			position: absolute;
			image-rendering: pixelated;
			cursor: pointer;
			filter: hue-rotate(calc(var(--hue, 0) * 1deg)) brightness(calc(var(--brightness, 100) * 1%)) grayscale(calc(var(--grayscale, 0) * 1%));
			transition: transform 0.1s;

			&:hover {
				&>div.description {
					width: fit-content;
					height: calc(var(--line-count, 1) * 40px);
					opacity: 100%;
					transform: translate(-4px, -4px)
				}
			}

			&>div.description {
				width: inherit;
				height: 0;
				background-color: #2B2B2BEE;
				border-radius: 4px;
				border-color: #1B1B1B;
				border-width: 4px;
				border-style: solid;
				opacity: 0%;
				position: absolute;
				overflow: hidden;
				transition: width, height, opacity, 0.15s;
				z-index: 2;
				margin-top: calc(var(--event-height, 1) * var(--scale, 1) * 28px);

				&>div {
					height: 30px;
					margin: 5px;
					padding-left: 5px;
					font-size: 16px;
					font-weight: bold;
					display: inline-block;
					width: calc(var(--text-box-width, 100) * 1%);

					&.left{
						text-align:left;
					}
					&.center{
						text-align:center;
					}
					&.right{
						text-align:right;
					}
					&.text {
					}

					&.box {
						color: #373737;
						background-color: #C9C9C9;
						border-radius: 4px;
					}
				}
			}

			&:hover {
				z-index: 1;
			}
		}

		&>.event {
			width: calc(var(--event-width, 1)*var(--scale, 1) * 28px);
			height: calc(var(--event-height, 1)*var(--scale, 1) * 28px);
			transform: translate(calc(var(--beat, 0) * var(--scale, 1) * 28px), calc(var(--y, 0) * var(--scale, 1) * 28px));
			background-size: auto calc(var(--scale, 1) * 28px * 8);
			background-position: calc(var(--event-x, 0) * var(--scale, 1) * -28px) calc((var(--event-y, 0) + 4) * var(--scale, 1) * -28px);

			&:active {
				transform: translate(calc(var(--beat, 0) * var(--scale, 1) * 28px), calc((var(--y, 0) * 28 + 2)*var(--scale, 1) * 1px));
				background-position: calc(var(--event-x, 0) * var(--scale, 1) * -28px) calc(var(--event-y, 0) * var(--scale, 1) * -28px);
			}
			&.sounds{
				background-image: var(--img, url(./assets/events/sounds.png));				
			}
			&.rooms{
				background-image: var(--img, url(./assets/events/rooms.png));				
			}
			&.decorations{
				background-image: var(--img, url(./assets/events/decorations.png));				
			}
			&.actions{
				background-image: var(--img, url(./assets/events/actions.png));				
			}

			&>div {
				&.condition-true {
					position: absolute;
					width: calc(var(--scale, 1) *12px);
					height: calc(var(--scale, 1) *12px);
					background-size: 100%;
					background-image: url(./assets/condition-true.png);

				}

				&.condition-false {
					position: absolute;
					width: calc(var(--scale, 1) *12px);
					height: calc(var(--scale, 1) *12px);
					background-size: 100%;
					background-image: url(./assets/condition-false.png);

				}

				&.condition-both {
					position: absolute;
					width: calc(var(--scale, 1) *12px);
					height: calc(var(--scale, 1) *12px);
					background-size: 100%;
					background-image: url(./assets/condition-both.png);

				}

				&.tag {
					position: absolute;
					width: calc(var(--scale, 1) *12px);
					height: calc(var(--scale, 1) *12px);
					transform: translate(0, calc(var(--event-height, 1) *28px - 12px));
					background-size: 100%;
					background-image: url(./assets/tag.png);
				}
			}
		}

		&>.beat {
			width: calc(((var(--tick, 1) + var(--delay, 0)) * 28 - 2) * var(--scale, 1) * 1px);
			height: calc(var(--scale, 1) * 28px);
			transform: translate(calc((var(--beat, 0) * 28 + 2) * var(--scale, 1) * 1px), calc(var(--y, 0) * var(--scale, 1) * 28px));
			background-image: url(./assets/beats/beat-middle.png);
			background-size:auto calc(var(--scale) * 28px);

			&::before {
				content: '';
				position: absolute;
				background-image: url(./assets/beats/beat-left.png);
				background-size:auto calc(var(--scale, 1) * 28px);
				transform: translate(calc(var(--scale, 1) * -6px), 0);
				width: calc(var(--scale, 1) *10px);
				height: inherit;
			}

			&::after {
				content: '';
				position: absolute;
				background-image: url(./assets/beats/beat-right.png);
				background-size:auto calc(var(--scale) * 28px);
				transform: translate(calc((var(--tick, 1) + var(--delay, 0)) * 28px - 6px), 0);
				transform: translate(calc(((var(--tick, 1) + var(--delay, 0)) * 28 - 6) * var(--scale, 1) * 1px), 0);
				width: calc(var(--scale, 1) *10px);
				height: inherit;
			}

			&>div {
				&.condition-true {
					position: absolute;
					width: calc(var(--scale, 1) *12px);
					height: calc(var(--scale, 1) *12px);
					transform: translate(calc(var(--scale, 1) * -2px), 0);
					background-size: 100%;
					background-image: url(./assets/condition-true.png);
					z-index: 0;
				}

				&.condition-false {
					position: absolute;
					width: calc(var(--scale, 1) *12px);
					height: calc(var(--scale, 1) *12px);
					transform: translate(calc(var(--scale, 1) * -2px), 0);
					background-size: 100%;
					background-image: url(./assets/condition-false.png);
					z-index: 0;
				}

				&.condition-both {
					position: absolute;
					width: calc(var(--scale, 1) *12px);
					height: calc(var(--scale, 1) *12px);
					transform: translate(calc(var(--scale, 1) * -2px), 0);
					background-size: 100%;
					background-image: url(./assets/condition-both.png);
					z-index: 0;
				}

				&.tag {
					position: absolute;
					width: calc(var(--scale, 1) *12px);
					height: calc(var(--scale, 1) *12px);
					transform: translate(-2px, calc((var(--event-height, 1)* 28 - 12) * var(--scale, 1) * 1px));
					background-size: 100%;
					background-image: url(./assets/tag.png);
					z-index: 0;
				}
			}

			&:hover {
				&::before {
					transform: translate(calc(var(--scale, 1) * -4px), 0);
					width: calc(var(--scale, 1) * 6px);
					background-image: url(./assets/beats/beat-pulse-start.png);
				}
				&>div.subdivision>div::before {
					opacity: 100%;
				}

				&>div.burnshot {
					transform: translate(calc((var(--tick, 1) * 28 - 11)*var(--scale,1) *1px), calc(var(--scale, 1) * -8px));
					width: calc(var(--scale, 1) * 18px);
					height: calc(var(--scale, 1) * 36px);
					background-size: 100%;
					background-image: url(./assets/beats/burnshot-hover-right.png);

					&::before {
						transform: translate(calc(((var(--tick, 0) + var(--interval)) * -28 + 7)*var(--scale,1)*1px), calc(var(--scale, 1) * 19px));
					}

					&::after {
						transform: translate(calc(((var(--interval)) * -28 + 7)*var(--scale,1)*1px), calc(var(--scale, 1) * 19px));
					}
				}
				&>div.classybeat>div {
					opacity: 100%;
				}

				&:not(div.classybeat){
					&::after {
						transform: translate(calc(((var(--tick, 1) + var(--delay, 0)) * 28 - 11)*var(--scale,1)*1px), calc(var(--scale, 1) * -8px));
						width: calc(var(--scale, 1) * 18px);
						height: calc(var(--scale, 1) * 36px);
					background-size: 100%;
						z-index: 1;
						background-image: url(./assets/beats/oneshot-hover-right.png);
					}

				}
			}

			&:active {
				transform: translate(calc((var(--beat, 0) * 28 + 2) * var(--scale, 1) * 1px), calc((var(--y, 0) * 28 + 2) * var(--scale, 1) * 1px));
				background-image: url(./assets/beats/beat-hover-middle.png);

				&::before {
					/* transform: translate(calc(var(--scale, 1) * -4px), 0);
					width: 6px; */
					background-image: url(./assets/beats/beat-hover-pulse-start.png);
				}
				&>div.holdbeat {
					background-image: url(./assets/beats/hold-hover-area.png);

					&::after {
						background-image: url(./assets/beats/hold-hover-right.png);
					}
				}
			}

			&>div.burnshot {
				position: absolute;
				background-image: url(./assets/beats/burnshot-right.png);
				background-size: 100%;
				transform: translate(calc((var(--tick, 1)*28 - 8)*var(--scale,1)*1px), 0);
				width: calc(var(--scale, 1) * 14px);
				height: inherit;

				&::before {
					content: '';
					position: absolute;
					width:calc(var(--scale, 1) * 6px);
					height: calc(var(--scale, 1) *6px);
					background-size: auto 100%;
					transform: translate(calc(((var(--tick, 0) + var(--interval)) * -28 + 4)*var(--scale,1)*1px), calc(var(--scale, 1) * 11px));
					background-image: url(./assets/beats/cross.png);
				}

				&::after {
					content: '';
					position: absolute;
					width:calc(var(--scale, 1) * 6px);
					height: calc(var(--scale, 1) *6px);
					background-size: auto 100%;
					transform: translate(calc(((var(--interval)) * -28 + 4)*var(--scale,1)*1px), calc(var(--scale, 1) * 11px));
					background-image: url(./assets/beats/cross.png);
				}
			}

			&>div.freezeshot {
				position: absolute;
				background-image: url(./assets/beats/freeze-hit.png);
				transform: translate(calc((var(--tick, 1) * 28 - 6)*var(--scale, 1) *1px), 0);
				width: calc(var(--scale, 1) * 10px);
				background-size:100%;
				height: inherit;

				&::before {
					content: '';
					position: absolute;
					width:calc(var(--scale, 1) * 6px);
					height: calc(var(--scale, 1) *6px);
					background-size: auto 100%;
					transform: translate(calc(((var(--interval)) * -28 + 2)*var(--scale, 1) *1px), calc(var(--scale, 1) *11px));
					background-image: url(./assets/beats/cross.png);
				}

				&::after {
					content: '';
					position: absolute;
					width:calc(var(--scale, 1) * 6px);
					height: calc(var(--scale, 1) *6px);
					background-size: auto 100%;
					transform: translate(calc(((var(--interval) - var(--delay)) * -28 + 2)*var(--scale, 1) *1px), calc(var(--scale, 1) *11px));
					background-image: url(./assets/beats/cross.png);
				}
			}

			&>div.skipshot {
				position: absolute;
				width: calc(((var(--tick, 1) * 2 - var(--delay, 0) - (var(--tick, 1) * ((var(--subdivision, 1) - 1) / var(--subdivision, 1)))) * 28 + 2)*var(--scale, 1) *1px);
				height: inherit;
				background-size: auto 100%;
				background-image: url(./assets/beats/skip-area.png);
				transform: translate(calc(((var(--tick, 1) + var(--delay, 0) + (var(--tick, 1) * ((var(--subdivision, 1) - 1) / var(--subdivision, 1)))) * 28 - 2)*var(--scale, 1) *1px), 0);
				z-index: -2;

				&::after {
					content: '';
					position: absolute;
					width: calc(var(--scale, 1) *10px);
					height: calc(var(--scale, 1) *28px);
					background-size: auto 100%;
					transform: translate(calc(((var(--tick, 1) * 2 - var(--delay, 0) - (var(--tick, 1) * ((var(--subdivision, 1) - 1) / var(--subdivision, 1)))) * 28 - 4)*var(--scale, 1) *1px), 0);
					background-image: url(./assets/beats/skip-right.png);
				}
			}

			&>div.subdivision {
				display: grid;
				grid-template-columns: repeat(calc(var(--subdivision, 1) - 1), auto);
				position: absolute;
				width: calc(((var(--tick, 1) * ((var(--subdivision, 1) - 1) / var(--subdivision, 1))) * 28 + 2)*var(--scale, 1) *1px);
				height: inherit;
				background-size: auto 100%;
				transform: translate(calc(((var(--tick, 1) + var(--delay, 0)) * 28 - 2)*var(--scale, 1) *1px), 0);
				background-image: url(./assets/beats/subdivision-area.png);
				z-index: -1;

				&>div {
					background-image: url(./assets/beats/hit.png);
					width: calc(var(--scale, 1) *10px);
					background-size: auto 100%;
					transform: translate(calc(((var(--tick, 1) * (1 / var(--subdivision, 1))) * 28 - 4)*var(--scale, 1) *1px), 0);
					z-index: 2;

					&::before {
						content: '';
						position: absolute;
						width: calc(var(--scale, 1) *6px);
						height: calc(var(--scale, 1) *28px);
						background-size: auto 100%;
						opacity: 0%;
						transform: translate(calc(((var(--tick, 1) + var(--delay, 0)) * -28 + 2)*var(--scale, 1) *1px), 0);
						background-image: url(./assets/beats/pulse.png);
					}
				}
			}

			&>div.classybeat {
				display: grid;
				grid-template-columns: repeat(6, calc((var(--tick, 1) / 3 - var(--swing, var(--tick, 1) / 6)) * var(--scale, 1) * 28px) calc((var(--swing, var(--tick, 1) / 6)) * var(--scale, 1) * 28px));
				position: absolute;
				width: calc(var(--tick, 1) * 28px);
				height: inherit;

				&>div {
					width:calc(var(--scale, 1) * 6px);
					height: inherit;
					transform: translate(calc(var(--scale, 1) * -4px), 0);
					background-size: auto 100%;
					opacity: 0%;
					background-image: url(./assets/beats/pulse.png);
					z-index: 1;
				}
			}

			&>div.holdbeat {
				position: absolute;
				width: calc(var(--hold, 1) * var(--scale, 1) * 28px);
				height: inherit;
				background-size: auto 100%;
				background-image: url(./assets/beats/hold-area.png);
				transform: translate(calc(((var(--tick, 1) + var(--delay, 0)) * 28 - 2)*var(--scale, 1) * 1px), 0);
				z-index: -2;

				&::after {
					content: '';
					position: absolute;
					width: calc(var(--scale, 1) *2px);
					height: calc(var(--scale, 1) * 28px);
					background-size: auto 100%;
					transform: translate(calc(var(--hold, 1) * var(--scale, 1) * 28px), 0);
					background-image: url(./assets/beats/hold-right.png);
				}
			}
		}

		&>div.pulse {
			width: 6px;
			height: 28px;
			transform: translate(calc(var(--beat, 0) * 28px - 2px), calc(var(--y, 0) * 28px));
			background-image: url(./assets/beats/pulse.png);
			z-index: 1;
		}
	}

	/* --stroke-width: 描边宽度 */
	/* --stroke-color: 描边颜色 */
	div.RDView>div.event>div.description>div.text,
	.stroke {
		font-weight: 800;
		text-shadow: calc(var(--stroke-width, 2)*1px) 0 0 var(--stroke-color, black), calc(var(--stroke-width, 2)*-1px) 0 0 var(--stroke-color, black), 0 calc(var(--stroke-width, 2)*1px) 0 var(--stroke-color, black), 0 calc(var(--stroke-width, 2)*-1px) 0 var(--stroke-color, black);
		width: calc(var(--text-box-width, 30) * 1%);
	}
</style>

<!-- <link rel="stylesheet" href="RDView.css"> -->

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