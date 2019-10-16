<template>
  <div id="course">
    <div>
      <h1>{{courseInfo.name}}</h1>
      <div>
        <span>{{courseInfo.description}}</span>
        <span>{{courseInfo.class}}</span>
      </div>
    </div>
    <div>
      <!-- <DrawingBoard :showColor="true" mode="two"></DrawingBoard> -->
      <iframe
        src="https://view.officeapps.live.com/op/embed.aspx?src=http%3A%2F%2Fvideo%2Ech9%2Ems%3A80%2Fbuild%2F2011%2Fslides%2FTOOL%2D532T%5FSutter%2Epptx&amp;wdAr=1.7777777777777777"
        width="915px"
        height="550.5px"
        frameborder="0"
      ></iframe>
    </div>
  </div>
</template>
<script>
import DrawingBoard from "@/components/DrawingBoard.vue";
export default {
  components: { DrawingBoard },
  data() {
    return {
      courseInfo: {
        name: this.$route.params.name,
        description: this.$route.params.description,
        class: this.$route.params.class
      }
    };
  },
  created() {
    console.log(this.courseInfo);
  }
};
</script>
<style lang="less" scoped>
#course {
  margin: 0;
  padding: 0;
  height: 100%;
}
</style>