<template>
    <li>
        <label>
            <input type="checkbox" :checked="todo.done" @change="handleCheck(todo.id)" />
            <span>{{todo.title}}</span>
        </label>
        <button class="btn btn-danger" @click="del(todo.id)">删除</button>
    </li>
</template>

<script>
export default {
    name:"MyItem",
    //接受父对象传达的对象
    props:["todo","deleteTodo","checkTodo"],
    methods:{
        handleCheck(id){
            //通知对应app组件将done取反
            this.checkTodo(id);
        },
        del(id)
        {
            if(confirm("确认删除吗？"))
            {
                this.deleteTodo(id);
            }
        }
    }
}
</script>

<style scoped>
li{
    list-style: none;
    height: 36px;
    line-height: 36px;
    padding: 0 5px;
    border-bottom:1px solid #ddd;
}
li label{
    float: left;
    cursor: pointer;
}
li label li input{
    vertical-align: middle;
    margin-right: 6px;
    position: relative;
    top:-1px;
}
li button{
    float: right;
    display: none;
    margin-top: 3px;

}
li:before{
    content: initial;
}
li:last-child{
    border-bottom:none;
}
li:hover{
    background-color: #ddd;
}
li:hover button{
    display: block;
}
</style>