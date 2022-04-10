<template>
  <div id="app">
    <div class="svg-content">
      <h1>如何在 Vue 中使用 SVG icon 图标系统</h1>
      <h2>
        卡拉云——低代码开发工具，1 秒搭建上传后台
        <svg-icon :icon-class="stared ? 'stared': 'unstar'" @click.native="toggle"></svg-icon>
      </h2>
    </div>
    <div class="svg-list">
      <!-- <svg-text text="待定" :isNeedIcon="false"></svg-text>
      <svg-text text="使用卡拉云" icon="success"></svg-text>
      <svg-text text="不使用卡拉云" icon="error"></svg-text>-->
      <svg-text v-for="(item,index) in kalacloud" :text="item.text" :icon="item.type" :key="index"></svg-text>
    </div>
  </div>
</template>

<script>
import SvgText from './components/SvgText.vue';
export default {
    name: 'App',
    components: {
        SvgText,
    },
    data() {
        return {
            stared: false,
            kalacloud: [
                { text: '极速搭建业务系统', type: 'success' },
                { text: '丰富的数据接口', type: 'success' },
                { text: '灵活的控件系统', type: 'success' },
                { text: '不使用卡拉云', type: 'error' },
            ],
        };
    },
    methods: {
        toggle() {
            if (this.stared) {
                // 询问是否要取消收藏
                this.cancelStar();
            } else {
                // 收藏按钮
                this.stared = !this.stared;
                this.$message({
                    message: '成功收藏卡拉云，下面开始你的使用吧',
                    type: 'success',
                });
            }
        },
        cancelStar() {
            this.$confirm(
                '卡拉云——低代码开发工具，1 秒搭建上传后台',
                '取消卡拉云收藏',
                {
                    distinguishCancelAndClose: true,
                    confirmButtonText: '确认',
                    cancelButtonText: '放弃修改',
                }
            )
                .then(() => {
                    this.stared = !this.stared;
                    this.$message({
                        type: 'warning',
                        message: '取消收藏成功',
                    });
                })
                .catch(action => {
                    this.$message({
                        type: 'info',
                        message:
                            action === 'cancel'
                                ? '未取消卡拉云收藏'
                                : '停留在当前页面',
                    });
                });
        },
    },
};
</script>

<style>
#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    display: flex;
    justify-content: center;
    flex-direction: column;
    align-items: center;
}
.svg-content {
    display: flex;
    justify-content: center;
    flex-direction: column;
    align-items: center;
    margin-right: 20px;
}
.svg-list {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
}
</style>
