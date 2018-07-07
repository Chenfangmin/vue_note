# vue_note

vue笔记

①  Vue数组操作(更新):

改变原数组:push()，pop()，shift()，unshift()，splice()，sort()，reverse();

eg:将一个数组添加一项:

vue person.push({

    name:'tom',
    
    sex:'男'
    
})

不更改原数组:filter()，concat()，slice();


②  v-if与v-show区别,v-cloak,v-once:

v-show: 

此用法与v-if基本一致,只不过是改变元素的CSS属性 display.

当v-show表达式的值为false时,元素会隐藏,查看DOM结构会看到元素上加载了内联样式 display:none. eg:

<div id="vue02">

	<p v-show="status===1">当status为1是显示该行</p>
  
</div>

<script>

	new Vue({
  
	el:"#vue02",
  
	data:{
  
		status:2
    
		}
    
	})
  
</script>

渲染后的结果为:

<p style="display:none">当status为1是显示该行</p>

v-cloak:
(不需要表达式，会在Vue实例结束编译时从绑定的HTML元素上移除，经常和css的display:none配合使用,[v-cloak]{display:none}), v-once指令(只渲染一次)

③  v-model对单选框(表单操作  radio)和复选按钮(checkbox)的操作:

④  修饰符:

.lazy  在输入框中，v-model默认是在input事件中同步输入框的数据(除了提示中介绍的中文输入法情况外)，使用修饰符 .lazy 会转变为在change事件中同步;  (eg:v-model.lazy='mesg')
 
.number   此修饰符可以将输入转换为Number类型，否则虽然你输入的是数字，但它的类型其实是String，比如在数字输入时会比较有用;(eg:v-model.number='mesg')

.trim 此修饰符可以自动过滤首尾输入的空格

⑤ Vue实例的生命周期:

Vue实例有一个完整的生命周期，也就是从开始创建、初始化数据、编译模板、挂载Dom、渲染→更新→渲染、卸载等一系列过程，我们称这是Vue的生命周期。通俗说就是Vue实例从创建到销毁的过程，就是生命周期。


钩子函数

每个钩子函数都在啥时间触发
(特别值得注意的是created钩子函数和mounted钩子函数的区别)

beforeCreate(创建前):

  在实例初始化之后，数据观测(data observer) 和 event/watcher 事件配置之前被调用。
  
created(已创建):

  实例已经创建完成之后被调用。在这一步，实例已完成以下的配置：数据观测(data observer)，属性和方法的运算， watch/event 事件回调。然而，挂载阶段还没开始，$el 属性目前不可见。
  
beforeMount(编译前):

  在挂载开始之前被调用：相关的 render 函数首次被调用。
  
mounted(编译后):

  el 被新创建的 vm.$el 替换，并挂载到实例上去之后调用该钩子。
  
beforeUpdate(更新前):

  数据更新时调用，发生在虚拟 DOM 重新渲染和打补丁之前。 你可以在这个钩子中进一步地更改状态，这不会触发附加的重渲染过程。
  
updated(更新后):

  由于数据更改导致的虚拟 DOM 重新渲染和打补丁，在这之后会调用该钩子。
  当这个钩子被调用时，组件 DOM 已经更新，所以你现在可以执行依赖于 DOM 的操作。然而在大多数情况下，你应该避免在此期间更改状态，因为这可能会导致更新无限循环。
 该钩子在服务器端渲染期间不被调用。
 
beforeDestroy(销毁前):

  实例销毁之前调用。在这一步，实例仍然完全可用。
  
destroyed(销毁后):

  Vue 实例销毁后调用。调用后，Vue 实例指示的所有东西都会解绑定，所有的事件监听器会被移除，所有的子实例也会被销毁。 该钩子在服务器端渲染期间不被调用。
