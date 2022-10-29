<template>
    <div class="student">
        <h2>学生姓名：{{ zsInfo.name }}</h2>
        <h2>学生年龄：{{ zsInfo.age }}</h2>
        <h2>学生性别：{{ zsInfo.sex }}</h2>
        <button @click="sendInfo">把学生信息传给学校</button>
    </div>
</template>

<script>
import emitter from '../emitt'
export default {
    name: 'Student',
    data() {
        return {
            zsInfo:{
                name: '张三',
                age: 18,
                sex: '男'
            }
        }
    },
    methods: {
        sendInfo() {
            emitter.emit('mittInfo',this.zsInfo)
        }
    }
}
</script>

<style lang="less" scoped>
.student {
    background-color: pink;
    padding: 5px;
    margin-top: 30px;
}
</style>