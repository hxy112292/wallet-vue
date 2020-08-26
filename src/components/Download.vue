<template>
  <div class="hello">
    <h1 style="font-size: 40px">
      <strong style="color: #448AFF">H </strong>
      <strong style="color: #FF3366">D </strong>
      <strong style="color: #43C391">- </strong>
      <strong style="color: #FFCC33">W </strong>
      <strong style="color: #448AFF">a </strong>
      <strong style="color: #43C391">l </strong>
      <strong style="color: #FF3366">l </strong>
      <strong style="color: #FFCC33">e </strong>
      <strong style="color: #448AFF">t </strong>
    </h1>
    <p style="font-size: large;margin: 0px 3% 0px 3%">HD-Wallet 是一个简单好用的区块链钱包，支持BTC/ETH/LTC/BCH/XRP等多个币种，还配备强大的策略助手来满足的您的投资需求。</p>
    <el-container>
      <el-main>
        <el-row :gutter="20">
          <el-col :md="24" :lg="7" :xl="10">
            <h2 style="margin: 0px">Android 安装包下载</h2>
            <p>版本：{{version}}</p>
            <el-button type="primary" @click="downloadApk" icon="el-icon-download">点击下载</el-button>
            <p><strong>或扫码下载：</strong></p>
            <vue-qr :text="downloadData.url" :margin="0" colorDark="#0d0d0d" colorLight="#fff" :logoSrc="downloadData.icon" :size="200"></vue-qr>
          </el-col>
          <el-col :lg="5" :xl="4" class="hidden-md-and-down">
            <el-image :src="imageUrl1"></el-image>
          </el-col>
          <el-col :lg="5" :xl="4" class="hidden-md-and-down">
            <el-image :src="imageUrl2"></el-image>
          </el-col>
          <el-col :lg="5" :xl="4" class="hidden-md-and-down">
            <el-image :src="imageUrl3"></el-image>
          </el-col>
        </el-row>
      </el-main>
    </el-container>

  </div>
</template>

<script>
import vueQr from 'vue-qr';
import 'element-ui/lib/theme-chalk/display.css';
export default {
  components: {
    vueQr
  },
  data() {
    return {
      downloadData: {
        url: this.$global.clubUrl + '/update/apk',
        icon: require('../assets/icon.png')
      },
      imageUrl1: require('../assets/wallet.png'),
      imageUrl2: require('../assets/invest-assistant.png'),
      imageUrl3: require('../assets/market.png'),
      imageUrl4: require('../assets/coin-detail.png'),
      version: ''
    }
  },
  name: 'Download',
  props: {
    msg: String
  },
  mounted() {
    this.getApkVersion();
  },
  methods: {
    getApkVersion () {
      console.log(this.$store.baseUrl);
      this.$axios.get(this.$global.clubUrl + '/update/version').then( res=> {
        this.version = res.data.result;
      })
    },
    downloadApk () {
      // window.open("https://www.hd-wallet.com:7070/update/apk")

      let url = this.$global.clubUrl + "/update/apk"
      let link = document.createElement('a')
      link.style.display = 'none'
      link.href = url
      link.setAttribute('download', 'hd-wallet_v_' + this.version.replace(/\./g, '_') + '.apk')

      document.body.appendChild(link)
      link.click()
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
  h3 {
    margin: 40px 0 0;
  }
  ul {
    list-style-type: none;
    padding: 0;
  }
  li {
    display: inline-block;
    margin: 0 10px;
  }
  a {
    color: #42b983;
  }
</style>
