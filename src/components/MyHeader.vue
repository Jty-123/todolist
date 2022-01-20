<template>
    <div class ="todo-header">
        <input type="text" placeholder="请输入你的任务名称，按回车键确认" v-model="title" @keyup.enter="addItem"/>

    </div>

</template>

<script>
import {nanoid} from "nanoid";
export default {
    name:"MyHeader",
    props:["receive"],
    data()
    {
        return {title:""};
    },
    methods:{
        addItem()
        {
            if(!this.title.trim()) return alert("输入不能为空");
            const todoObj = {id:nanoid(),title:this.title,done:false};
            this.receive(todoObj);
            this.title="";
        }
    }
    
}
</script>

<style scoped>
 
.todo-header input{
    width: 560px;
    height: 28px;
    font: 14px;
    border: 1px solid #ccc;
    border-radius: 4px;
    padding: 4px 7px;
    }
.todo-header input:focus{
    outline: none;
    border-color: rgba(82, 168, 236, 0.8);
    }
</style>