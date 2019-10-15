<template>
  <div class="home">
    <van-row type="flex" justify="center">
      <van-col span="6">
        <HomeNav></HomeNav>
      </van-col>
      <van-col span="18">
        <van-row type="flex" justify="space-around">
          <van-col span="10">
            <ShowCard title="Create" @click.native="showCreatCard=!showCreatCard"></ShowCard>
          </van-col>
          <van-col span="10">
            <ShowCard title="Impromptu"></ShowCard>
          </van-col>
        </van-row>
      </van-col>
    </van-row>
    <van-popup v-model="showCreatCard" round class="creatCard" position="right">
      <h1>添加</h1>
      <van-cell-group>
        <van-cell>
          <template>
            <van-field v-model="newCourse.name" placeholder="课程名称" />
          </template>
        </van-cell>
        <van-cell>
          <template>
            <van-field v-model="newCourse.description" placeholder="简单描述" type="textarea" autosize/>
          </template>
        </van-cell>
        <van-cell>
          <template>
            <van-field
              clickable
              :value="newCourse.class"
              placeholder="分类"
              @click="showPicker = true"
            />
            <van-popup v-model="showPicker" position="bottom" :overlay="false">
              <van-picker
                show-toolbar
                :columns="classColumns"
                @cancel="showPicker = false"
                @confirm="onConfirm"
              />
            </van-popup>
          </template>
        </van-cell>
        <van-cell>
          <van-button type="primary" @click="submitCreatCourse()">创建课程</van-button>
        </van-cell>
      </van-cell-group>
    </van-popup>
  </div>
</template>

<script>
// @ is an alias to /src
import ShowCard from "@/components/ShowCard.vue";
import HomeNav from "@/components/HomeNav.vue";

export default {
  name: "home",
  components: { ShowCard, HomeNav },
  data() {
    return {
      showCreatCard: false,
      showPicker: false,
      classColumns: ["计算机原理", "操作系统", "软件工程导论"],
      newCourse: {
        name: "",
        description: "",
        class: ""
      },
      courseList:{

      }
    };
  },
  methods: {
    //选择课程分类点击确定
    onConfirm(value) {
      this.newCourse.class = value;
      this.showPicker = false;
    },
    //提交确定
    submitCreatCourse(){
      console.log(this.newCourse);
    }
  }
};
</script>
<style lang="less" scoped>
.creatCard {
  width: 40%;
  height: 100vh;
}
</style>
