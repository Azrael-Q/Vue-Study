<template>
    <div class="school">
        <h2>学校名称：{{ name }}</h2>
        <h2>学校地址：{{ address }}</h2>
        <span>
            <h2>学生信息</h2>
            <ul>
                <li v-for="stu in studentInfo">
                    <span>身份证号码：{{stu.id}}</span>
                    <br>
                    <span>姓名：{{stu.name}}</span>
                    <br>
                    <span>年龄：{{stu.age}}</span>
                    <br>
                    <span>性别：{{stu.sex}}</span>
                    <hr/>
                </li>
            </ul>
        </span>
    </div>
</template>

<script>
import emitter from '../emitt'
export default {
    name: 'School',
    data() {
        return {
            name: '尚硅谷',
            address: '北京',
            studentInfo: {}
        }
    },
    mounted() {
        emitter.on('mittInfo', (data) => {
            this.studentInfo = data
        })
    },
    beforeDestroy() {
        emitter.off('mittInfo')
    },
}
</script>

<style lang="less" scoped>
.school {
    background-color: skyblue;
    padding: 5px;
}
</style>