<template>
  <div id="app">
    <input type="text" v-model="zipCode" placeholder="000-0000" />
    <!-- <input type="text" v-model="address"> 削除-->
    <button @click="autoCompleteAddress(zipCode)">住所自動入力</button>
    <!-- <button @click="autoCompleteAddress(zipCode)">住所自動入力</button> 引数削除 -->
    <!-- <router-view /> 削除 -->
    <p>住所：{{address}}</p>
    <!-- 閉じタグ追加 -->
  </div>
</template>

<script>
import axios from 'axios';
export default{
  data() {
    return {
      zipCode: '',
      address: '',
    }
  },
  methods: {
    // autoCompleteAddress(zipCode){
    //   this.axios.get(`https://api.zipaddress.net/?zipcode=${zipcode}`) //this.axios -> axios
    //   then.((response)=>{ //then.() -> .then()
    //     this.address = response.data.fullAddress
    //   })
    //   .catch(() => {
    //     this.address = ''
    //   })
    // }
    autoCompleteAddress(zipcode){
      console.log(zipcode);
      // axios.get(`エンドポイントURL/postcodes/${zipcode}?クエリパラメータ(apiKey)=値`) となります
      axios.get(`https://api.postcodes-jp.com/api/v4/postcodes/${zipcode}?1000001 -G -v(apiKey)=Dc4zzV1p2WjbFgiHlzYoIsXHYYsu0dSU4wSliG6`)
      .then((response)=>{
        console.log(response); //住所の取り出しを行う
        // こちらの教材の（https://coachtech-lms.com/javascript/javascript-object/2718/）
        this.address = response.data.fullAddress;
      })
      .catch(() => {
        this.address = ''
      });
    }
  }
}
</script>
<style>
html, body, div, span, object, iframe,
h1, h2, h3, h4, h5, h6, p, blockquote, pre,
abbr, address, cite, code,
del, dfn, em, img, ins, kbd, q, samp,
small, strong, sub, sup, var,
b, i,
dl, dt, dd, ol, ul, li,
fieldset, form, label, legend,
table, caption, tbody, tfoot, thead, tr, th, td,
article, aside, canvas, details, figcaption, figure,
footer, header, hgroup, menu, nav, section, summary,
time, mark, audio, video {
    margin:0;
    padding:0;
    border:0;
    outline:0;
    font-size:100%;
    vertical-align:baseline;
    background:transparent;
}

body {
    line-height:1;
}

article,aside,details,figcaption,figure,
footer,header,hgroup,menu,nav,section {
    display:block;
}

nav ul {
    list-style:none;
}

blockquote, q {
    quotes:none;
}

blockquote:before, blockquote:after,
q:before, q:after {
    content:'';
    content:none;
}

a {
    margin:0;
    padding:0;
    font-size:100%;
    vertical-align:baseline;
    background:transparent;
}

/* change colours to suit your needs */
ins {
    background-color:#ff9;
    color:#000;
    text-decoration:none;
}

/* change colours to suit your needs */
mark {
    background-color:#ff9;
    color:#000;
    font-style:italic;
    font-weight:bold;
}

del {
    text-decoration: line-through;
}

abbr[title], dfn[title] {
    border-bottom:1px dotted;
    cursor:help;
}

table {
    border-collapse:collapse;
    border-spacing:0;
}

/* change border colour to suit your needs */
hr {
    display:block;
    height:1px;
    border:0;  
    border-top:1px solid #cccccc;
    margin:1em 0;
    padding:0;
}

input, select {
    vertical-align:middle;
}
</style>