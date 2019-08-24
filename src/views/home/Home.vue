<template>
  <div id="home" class="wrapper">
    <nav-bar class="home-nav"><div slot="center">购物街</div></nav-bar>
    <home-swiper :banners="banners"/>
    <recommend-view :recommends="recommends"/>
    <feature-view/>
    <tab-control class="tab-control"
                 :titles="['流行', '新款', '精选']"
                 @tabClick="tabClick"/>
    <good-list :goods="showGoods"></good-list>
    <ul>
      <li>信息1</li>
      <li>信息2</li>
      <li>信息3</li>
      <li>信息4</li>
      <li>信息5</li>
      <li>信息6</li>
      <li>信息7</li>
      <li>信息8</li>
      <li>信息9</li>
      <li>信息10</li>
      <li>信息11</li>
      <li>信息12</li>
      <li>信息13</li>
      <li>信息14</li>
      <li>信息15</li>
      <li>信息16</li>
      <li>信息17</li>
      <li>信息18</li>
      <li>信息19</li>
      <li>信息20</li>
      <li>信息21</li>
      <li>信息22</li>
      <li>信息23</li>
      <li>信息24</li>
      <li>信息25</li>
      <li>信息26</li>
      <li>信息27</li>
      <li>信息28</li>
      <li>信息29</li>
      <li>信息30</li>
      <li>信息31</li>
      <li>信息32</li>
      <li>信息33</li>
      <li>信息34</li>
      <li>信息35</li>
      <li>信息36</li>
      <li>信息37</li>
      <li>信息38</li>
      <li>信息39</li>
      <li>信息40</li>
      <li>信息41</li>
      <li>信息42</li>
      <li>信息43</li>
      <li>信息44</li>
      <li>信息45</li>
      <li>信息46</li>
      <li>信息47</li>
      <li>信息48</li>
      <li>信息49</li>
      <li>信息50</li>
      <li>信息51</li>
      <li>信息52</li>
      <li>信息53</li>
      <li>信息54</li>
      <li>信息55</li>
      <li>信息56</li>
      <li>信息57</li>
      <li>信息58</li>
      <li>信息59</li>
      <li>信息60</li>
      <li>信息61</li>
      <li>信息62</li>
      <li>信息63</li>
      <li>信息64</li>
      <li>信息65</li>
      <li>信息66</li>
      <li>信息67</li>
      <li>信息68</li>
      <li>信息69</li>
      <li>信息70</li>
      <li>信息71</li>
      <li>信息72</li>
      <li>信息73</li>
      <li>信息74</li>
      <li>信息75</li>
      <li>信息76</li>
      <li>信息77</li>
      <li>信息78</li>
      <li>信息79</li>
      <li>信息80</li>
      <li>信息81</li>
      <li>信息82</li>
      <li>信息83</li>
      <li>信息84</li>
      <li>信息85</li>
      <li>信息86</li>
      <li>信息87</li>
      <li>信息88</li>
      <li>信息89</li>
      <li>信息90</li>
      <li>信息91</li>
      <li>信息92</li>
      <li>信息93</li>
      <li>信息94</li>
      <li>信息95</li>
      <li>信息96</li>
      <li>信息97</li>
      <li>信息98</li>
      <li>信息99</li>
      <li>信息100</li>
    </ul>
  </div>
</template>

<script>
  import HomeSwiper from './childComps/HomeSwiper'
  import RecommendView from './childComps/RecomendView'
  import FeatureView from './childComps/FeatureView'

  import NavBar from 'components/common/navbar/NavBar'
  import TabControl from 'components/content/tabControl/TabControl'
  import GoodList from 'components/content/goods/GoodsList'

  import { getHomeMultidata, getHomeGoods } from "network/home"

  export default {
    name: "Home",
    components: {
      HomeSwiper,
      RecommendView,
      FeatureView,
      NavBar,
      TabControl,
      GoodList
    },
    data() {
      return {
        banners: [],
        recommends: [],
        goods: {
          'pop': {page: 0, list: []},
          'new': {page: 0, list: []},
          'sell': {page: 0, list: []},
        },
        currentType: 'pop',
      }
    },
    computed: {
      showGoods() {
        return this.goods[this.currentType].list
      }
    },
    created() {
      // 1.请求多个数据
      this.getHomeMultidata()

      // 2.请求商品数据
      this.getHomeGoods('pop')
      this.getHomeGoods('new')
      this.getHomeGoods('sell')
    },
    methods: {
      /**
       * 事件监听相关的方法
       */
      tabClick(index) {
        switch (index) {
          case 0:
            this.currentType = 'pop'
            break
          case 1:
            this.currentType = 'new'
            break
          case 2:
            this.currentType = 'sell'
            break
        }
      },
      /**
       * 网络请求相关的方法
       */
      getHomeMultidata() {
        getHomeMultidata().then(res => {
          // this.result = res;
          this.banners = res.data.banner.list;
          this.recommends = res.data.recommend.list;
        })
      },
      getHomeGoods(type) {
        const page = this.goods[type].page + 1
        getHomeGoods(type, page).then(res => {
          this.goods[type].list.push(...res.data.list)
          this.goods[type].page += 1
        })
      }
    }
  }
</script>

<style scoped>
  #home {
    width: 100%;
    padding-top: 44px;
    height: 100vh;
    position: relative;
  }

  .home-nav {
    background-color: var(--color-tint);
    color: #fff;

    position: fixed;
    left: 0;
    right: 0;
    top: 0;
    z-index: 9;
  }

  .tab-control {
    /*position: sticky;*/
    position: fixed;
    top: 44px;
    z-index: 9;
  }

  .content {
    overflow: hidden;

    position: absolute;
    top: 44px;
    bottom: 49px;
    left: 0;
    right: 0;
  }

  /*.content {*/
  /*height: calc(100% - 93px);*/
  /*overflow: hidden;*/
  /*margin-top: 44px;*/
  /*}*/
</style>
