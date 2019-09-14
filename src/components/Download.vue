<template>
  <div class="hello">
    <h1>纯前端实现下载</h1>
    <ul>
      <li v-for="(item, index) in arr" :key="index">
        <img :src="item.path" alt="item.name">
        <button @click="download(item.path, item.name)">下载</button>
      </li>
    </ul>
  </div>
</template>

<script>
import axios from 'axios';
export default {
  name: 'Download',
  props: {
    msg: String
  },
  data() {
    return {
      arr: [
        {
          name: '性感',
          path: 'https://cdn.jsdelivr.net/gh/qiang520184/fe-download-cdn@1.0/1.jpg'
        },
        {
          name: '兔女郎',
          path: 'https://cdn.jsdelivr.net/gh/qiang520184/fe-download-cdn@1.0/2.jpg'
        },
        {
          name: '可爱',
          path: 'https://cdn.jsdelivr.net/gh/qiang520184/fe-download-cdn@1.0/3.jpg'
        },
        {
          name: '清新',
          path: 'https://cdn.jsdelivr.net/gh/qiang520184/fe-download-cdn@1.0/4.jpg'
        }
      ]
    }
  },
  methods: {
    download(item, name) {
      let url = item.slice(item.indexOf('@1.0/')+4);
      console.log(url)
      axios.get(`/api${url}`,{
        responseType: 'blob'
      }).then(res => {
        var fileReader = new FileReader();
        fileReader.readAsDataURL(res.data);
        fileReader.onprogress = function (event) {
          // console.log(event, 'event')
        }
        fileReader.onload = function () {
          let a = document.createElement("a");
          a.href = this.result;
          a.setAttribute("download", name);
          a.click();
        }
      })
      // console.log(item)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang='less'>
h3 {
  margin: 40px 0 0;
}
ul {
  height: auto;
  margin: 0 auto;
  display: flex;
  align-items: center;
  display: flex;
  flex-direction: column;
}

ul li {
  list-style: none;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

ul li img {
  width: auto;
  height: 300px;
}
ul li button {
  width: 60px;
  height: 32px;
  margin: 20px 0;
  border: 0;
  outline: none;
  border: 1px solid #ccc;
  border-radius: 5px;
}
</style>
