<template>
    <div class="student">
        <ul>
            <li v-for="info in arr">
                <h2>学生姓名：{{ info.name }}</h2>
                <h2>学生年龄：{{ info.age }}</h2>
                <h2>学生性别：{{ info.sex }}</h2>
            </li>
        </ul>
        <button @click="sendInfo">把学生信息传给学校</button>
    </div>
</template>

<script>
import emitter from '../emitt'
import { nanoid } from 'nanoid'
export default {
    name: 'Student',
    data() {
        return {
            arr: [
                {
                    id: nanoid(),
                    name: '张三',
                    age: 18,
                    sex: '男'
                },
                {
                    id: nanoid(),
                    name: '李四',
                    age: 20,
                    sex: '女'
                }
            ]
        }
    },
    methods: {
        sendInfo() {
            // console.log(this.$data)
            emitter.emit('mittInfo', this.arr)
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

.student button {
    height: 30px;
}
</style>