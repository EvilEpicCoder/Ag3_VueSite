<template>
<div id="menu">

  <!-- <label>Поиск : {{ search }}</label>
  <input  id="suckThis" v-model="search" type="text" v-on:keyup="keyPress(search)" v-on:keyup.enter="goGo()"/>
  <button class="search" autofocus v-on:click="update(context.that)">Поиск</button>
  <button class="search" autofocus v-on:click="updateCountry">updateCountry</button> -->
</div>
</template>

<script>
export default {
  // props: [
  //   'geo',
  //   'weatherData',
  //   'context',
  //   'update'
  // ],
  // data () {
  //   return {
  //     search: {
  //       data: 'Ukraine, Kiev'
  //     }
  //   }
  // },
  // methods: {
  //   updateCountry: function () {
  //     alert(this.search.data)
  //     this.geo.country = 'Ukraine'
  //     this.geo.city = 'Odessa'
  //   },
  //   keyPress: function (ele) {
  //     this.search.data = ele.target.value
  //     console.log(this.search.data.split(','))
  //     if (this.search.data[0] !== undefined && this.search.data[0].lenght > 2) {
  //       if (this.search.data[1] !== undefined && this.search.data[1].lenght > 2) {
  //         this.geo.country = this.search.data[0]
  //         this.geo.city = this.search.data[1]
  //         this.update()
  //       }
  //     }
  //   }
  // },
  // computed: {
  //   goGo: function (ele) {
  //     this.search.data = ele.target.value
  //     console.log(this.search.data.split(','))
  //     if (this.search.data[0] !== undefined && this.search.data[0].lenght > 3) {
  //       if (this.search.data[1] !== undefined && this.search.data[1].lenght > 3) {
  //         this.geo.country = this.search.data[0]
  //         this.geo.city = this.search.data[1]
  //         this.update()
  //       }
  //     }
  //   }
  // }
}
</script>

<style>
/*#menu{
  display: flex;
  height: 80px;
  width:400px;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  position: relative;
}*/
/*input:focus, label ,button.search{
position: absolute;
font-size: 12px;
color: rgba(0,0,0,.50);
top: 0px;
left: 30px;
width: 180px;
z-index: -1;
transition: .15s all ease-in-out;
font-size: 10px;
outline: none;
transform: scale(1.05);
margin-top: 10px;

}
label {
  z-index: -1;
  position: absolute;
  font-size: 12px;
  color: rgba(0,0,0,.50);
  top: 10px;
  left: 30px;
}
button.search {
  width:80px;
  height:30px;
  z-index: 1;
  position: relative;
  font-size: 12px;
  color: rgba(0,0,0,.50);
  top: 0px;
  left: 260px;
}
input {
position: absolute;
top: 8px;
left: 190px;
width: 50px;
height: 30px;
color: rgba(0,0,0,.70);
border: 1px solid rgba(0,0,0,.12);
transition: .15s all ease-in-out;
background: white;
}*/

</style>
