这几天在封装组件时发现一些问题，展示数据的表格上都会有一些筛选项，选择之后点击搜索，会刷新下面表格的数据，这是一个很普通的需求。

但这里我需要将上述的筛选项封装成一个独立的脱离业务`React`组件，

这里，我们需要使用一种变通的方式来处理，也就是说，不需要为它绑定任何值，但需要设置一个`key`，当`key`变化时，组件会被重新渲染，利用这种思路，在`RangePicker`中设置如下：

```javascript
<RangePicker 
  className="w-full i-block"
  allowClear
  showTime
  format="YYYY-MM-DD HH:mm:ss"
  style={{width: '100%'}}
  key={rangePicker}  // 这里是关键
  onOk={(value) => handleSearchKeyChange(
		_v.field, 
		[value[0]._d.getTime(), value[1]._d.getTime()]
  )}
/>
```

在当前组件中，我们需要设置一个`state`来控制该组件

```javascript
const [ rangePicker, setRangePicker ] = useState<number>(0);
```

在重置按钮点击事件中，我们更新这个`state`，传入当前的时间戳

```javascript
const handleResetEvent = () => {
...
	// 处理RangePicker组件的选中值清空操作
	setRangePicker(new Date().getTime());
...
}
```

当`rangePicker`改变时，组件就是自动更新，这样就可以做到清空值的目的，实际上是组件被卸载然后又重新被加载的过程...
