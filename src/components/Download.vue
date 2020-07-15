<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <el-container>
      <el-main>
        <el-row :gutter="20">
          <el-col :sm="24" :lg="8">
            <h2>Android 安装包下载</h2>
            <el-button type="primary" @click="downloadApk">点击下载</el-button>
            <h3>或扫码下载：</h3>
            <br>
            <vue-qr :text="downloadData.url" :margin="0" colorDark="#0d0d0d" colorLight="#fff" :logoSrc="downloadData.icon" :size="200"></vue-qr>
          </el-col>
          <el-col :span="4" class="hidden-sm-and-down">
            <el-image :src="imageUrl1"></el-image>
          </el-col>
          <el-col :span="4" class="hidden-sm-and-down">
            <el-image :src="imageUrl2"></el-image>
          </el-col>
          <el-col :span="4" class="hidden-sm-and-down">
            <el-image :src="imageUrl3"></el-image>
          </el-col>
          <el-col :span="4" class="hidden-sm-and-down">
            <el-image :src="imageUrl4"></el-image>
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
        url: 'https://www.hd-wallet.com:7070/update/apk',
        icon: require('../assets/icon.png')
      },
      imageUrl1: require('../assets/wallet.png'),
      imageUrl2: require('../assets/invest-assistant.png'),
      imageUrl3: require('../assets/market.png'),
      imageUrl4: require('../assets/coin-detail.png')
    }
  },
  name: 'Download',
  props: {
    msg: String
  },
  methods: {
    downloadApk () {
      // window.open("https://www.hd-wallet.com:7070/update/apk")

      let url = "https://www.hd-wallet.com:7070/update/apk"
      let link = document.createElement('a')
      link.style.display = 'none'
      link.href = url
      link.setAttribute('download', 'app-debbug.apk')

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
