<template>
    <div class="richText">
        <textarea id="demo" style="display: none;"></textarea>
        <button type="button" class="layui-btn" @click="submit">提交留言</button>
    </div>
</template>

<script>
    export default {
        name: "richText",
        data(){
            return {
                layedit: null,
                index: 0,
            }
        },
        methods: {
            submit(){
                this.$emit("Sub", this.layedit.getContent(this.index));
            }
        },
        mounted() {
            layui.use('layedit', () => {
                this.layedit = layui.layedit;
                this.index = this.layedit.build('demo', {
                    tool: ['face'],
                    height: 150 //设置编辑器高度
                }); //建立编辑器
            });
        }
    }
</script>

<style scoped lang="less">
    .layui-btn{
        margin-top: 15px;
    }
</style>
