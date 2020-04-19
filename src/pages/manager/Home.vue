<template>
  <div class="home">
    <van-nav-bar
      title="山野人家农产品店"
    />
    <van-row>
      <img style="width:100%" src="../../assets/images/product.jpg" alt="">
    </van-row>
    <van-row>
      <van-grid :column-num="3">
        <!-- <van-grid-item
          @click="findProduct(c,index)"
          v-for="(c, index) in imageList"
          :key="c.id"
          :text="c.icon"
        /> -->
        <van-grid-item
          @click="findProduct(c,index)"
          v-for="(c, index) in categories"
          :key="c.id"
          :text="c.name"
        >
        </van-grid-item>
      </van-grid>
    </van-row>
  </div>
</template>
<script>
import {mapState,mapActions} from 'vuex'
export default {
  data() {
    return {
      imageList:[
        {
          id:1,
          icon:"../../assets/images/home.jpg"
        },
        {
          id:2,
          icon:"2"
        },
        {
          id:3,
          icon:"3"
        },
        {
          id:4,
          icon:"4"
        }
      ]
    }
  },
  created(){
    this.findAllCategories();
  },
  computed:{
    ...mapState("category",["categories"]),
  },
  methods:{
    ...mapActions("category",["findAllCategories"]),
    findProduct(category,index){
      this.$router.push({name:"product",query:{category,index}})
    }
  }
}
</script>