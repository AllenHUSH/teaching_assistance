<template>
  <div
    class="showCard"
    :style="css_div"
    :bgcolor="bgcolor"
    :width="width"
    :height="height"
    :icon="icon"
    :title="title"
    :color="color"
    :titleSize="titleSize"
    :content="content"
  >
    <div>
      <h1 :style="{'line-height':height,'font-size':titleSize}">
        <van-icon id="icon" :name="icon" />
        {{title}}
      </h1>
      <span :style="{'bottom':'calc('+height+'/2)'}">{{content}}</span>
    </div>
  </div>
</template>

<script>
/**
 * 接口说明文档
 * title:标题，默认为空
 * content:辅助说明，默认为空
 * bgcolor:背景色，默认为#f88
 * width:卡片宽度，默认400px
 * height:卡片高度，默认150px
 * titleSize:标题字体大小，默认40px
 * color:字体颜色，默认为#fff
 */
export default {
  props: {
    title: String,
    content: String,
    bgcolor: {
      type: String,
      default: "rgb(255, 134, 134)"
    },
    width: {
      type: String
      //   default: "400px"
    },
    height: {
      type: String,
      default: "150px"
    },
    icon: String,
    titleSize: {
      type: String,
      default: "40px"
    },
    color: {
      type: String,
      default: "#fff"
    }
  },
  data() {
    return {
      css_div: {
        background: this.bgcolor,
        width: this.width,
        height: this.height,
        color: this.color
      },
    };
  }
};
</script>
<style lang="less" scoped>
.showCard {
  border-radius: 30px;
  text-align: center;
  div {
    padding: 0 20px;
    h1 {
      white-space: nowrap;
      overflow: hidden;
      text-overflow: ellipsis;
    }
    #icon {
      display: inline;
    }
    span {
      position: relative;
      white-space: nowrap;
      overflow: hidden;
      text-overflow: ellipsis;
    }
  }
}
</style>
