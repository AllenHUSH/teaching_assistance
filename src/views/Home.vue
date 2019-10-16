<template>
  <!-- ---------------------------------------------------------------------------主视图 -->
  <div class="home">
    <!-- -------------------------------------------------------------------左侧导航栏布局 -->
    <div id="left">
      <HomeNav></HomeNav>
    </div>
    <!-- -------------------------------------------------------------------右侧操作区布局 -->
    <div id="right">
      <div class="showBox">
        <ShowCard title="Create" @click.native="showCreatCard=!showCreatCard"></ShowCard>
      </div>
      <!-- for循环自动生成 -->
      <div class="showBox" v-for="(item, index) in courseList" :key="index">
        <ShowCard
          :title="item.name"
          :content="item.description"
          :bgcolor="item.bgcolor"
          @click.native="toCourse(item)"
        ></ShowCard>
      </div>
    </div>

    <!-- ---------------------------------------------------------------------------新建课程卡片 -->
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
            <van-field v-model="newCourse.description" placeholder="简单描述" type="textarea" autosize />
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
        class: "",
        bgcolor: ""
      },
      courseList: [
        {
          name: "Impromptu",
          description: "开始你的即兴演讲",
          class: "",
          bgcolor: "#4f4f4f"
        },
        {
          name: "算法（一）",
          description: "算法概论",
          class: "计算机",
          bgcolor: "#66ff00"
        },
        {
          name: "人工智能（六）",
          description: "机器学习和人工智能的关系",
          class: "软件",
          bgcolor: "#6600ff"
        },
        {
          name: "人工智能（七）",
          description: "三种机器学习方法",
          class: "软件",
          bgcolor: "#66aaff"
        }
      ]
    };
  },
  methods: {
    toCourse(item) {
      this.$router.push({
        name: "Course",
        params: {
          name: item.name,
          description: item.description,
          class: item.class,
          bgcolor: item.class
        }
      });
    },
    //选择课程分类点击确定
    onConfirm(value) {
      this.newCourse.class = value;
      this.showPicker = false;
    },
    //提交确定
    submitCreatCourse() {
      console.log(this.newCourse);
    }
  }
};
</script>
<style lang="less" scoped>
.home {
  margin: 0;
  padding: 0;
  #left {
    width: 30vw;
    float: left;
  }
  #right {
    width: 70vw;
    float: left;
    display: flex;
    display: -webkit-flex;
    flex-wrap:wrap;
    justify-content: space-around;
    .showBox {
      width: 45%;
    }
    .creatCard {
      width: 40%;
      height: 100vh;
      .showBox {
        width: 100px;
      }
    }
  }
}
</style>
