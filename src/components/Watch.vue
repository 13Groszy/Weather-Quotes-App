<template>
    <div>
    <p>{{localTime}}</p>
    <p>{{date}}</p>
    </div>
</template>

<script>
export default {
    name: 'Watch',
    data() {
        return {
            localTime: '',
            date:'',
        }
    },
    methods:{
    showLocaleTime: function () {
      var time = this;
      setInterval(function () {
       time.localTime = new Date().toLocaleTimeString();
       let date = new Date();
       let day = date.getDate();
       let month = date.getMonth();
       let year = date.getFullYear();
       time.date = day + '/' + month + '/' + year
    }, 1000);
   }
  },
 created () {
  this.showLocaleTime()
        }
}
</script>