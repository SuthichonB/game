<template>
   <div href="#" class="text-light">
   <button v-on:click="randomC(0,3) ,create(p,m)">start</button> <br>
   <button v-bind:disabled="end" v-on:click="random(),check()">Acttack</button> <button v-bind:disabled="end" v-on:click="srandom(),check()">Spacial Acttack</button> 
   <div >
   <div class="row">
   </div>
    <div  class="row align-items-end">
     <div class="col-sm" >
       <div v-if="php>=0">
       <div v-if="animation==0"> <img :src="player[p].img" :height="php" alt=""> </div>
       <div v-if="animation==1"> <img :src="player[p].img1" :height="php" alt=""> </div>
       <div v-if="animation==2"> <img :src="player[p].img2" :height="php" alt=""> </div>
        <div v-if="mhp>0&&php>0">
         {{php}} <br>
          - {{mpower}}
         </div>
       </div>
     </div>
     <div class="col-sm">
        <img src="https://i.imgur.com/yKlSQK1.png" height="800" alt="">
         <div v-if="php<=0&&mhp>0"> <h3> {{monter[m].name}} Win </h3></div>
         <div v-if="mhp<=0&&php>0"> <h3> {{player[p].name}} Win </h3></div>
         <div v-if="mhp==0&&php==0"><h3>  Draw  </h3></div>
         <div v-if="mhp>0&&php>0"><h3>  {{player[p].name}}  VS  {{monter[m].name}} </h3></div>
     </div>
     <div class="col-sm">
        <div v-if="mhp>=0"> <img :src="monter[m].img" :height="mhp" alt=""> </div>
        <div v-if="mhp>0&&php>0">
           {{mhp}}<br>
         - {{ppower}}
         </div>
      </div>
    </div>
   </div>
  </div>
</template>
<script>
export default {
  name: 'HelloWorld',
  data: function() {
      return{
        player : [{name: 'Goku',hp: 350,img:'https://cdn.discordapp.com/attachments/709406382134263882/745701713880809493/pngegg_21.png',img1:'https://cdn.discordapp.com/attachments/709406382134263882/745701713880809493/pngegg_21.png',img2:'https://cdn.discordapp.com/attachments/709406382134263882/745701713880809493/pngegg_21.png'},
                  {name: 'Luffy',hp: 300,img:'https://cdn.discordapp.com/attachments/709406382134263882/745699838108106912/pngegg_16.png',img1:'https://cdn.discordapp.com/attachments/709406382134263882/745699838108106912/pngegg_16.png',img2:'https://cdn.discordapp.com/attachments/709406382134263882/745699838108106912/pngegg_16.png'} ,
                  {name: 'Iron Man',hp: 400,img:'https://i.pinimg.com/originals/9e/06/97/9e0697990828bb8319be8105c939b108.gif?fbclid=IwAR17mTMcT3DTLSe5tBVAgOfUNOpwmnx6y6KrjvJDWD1eTBlXfsyjfXOhcg0',img1:'https://i.pinimg.com/originals/9e/06/97/9e0697990828bb8319be8105c939b108.gif?fbclid=IwAR17mTMcT3DTLSe5tBVAgOfUNOpwmnx6y6KrjvJDWD1eTBlXfsyjfXOhcg0',img2:'https://i.pinimg.com/originals/9e/06/97/9e0697990828bb8319be8105c939b108.gif?fbclid=IwAR17mTMcT3DTLSe5tBVAgOfUNOpwmnx6y6KrjvJDWD1eTBlXfsyjfXOhcg0'},
                  {name: 'Naruto',hp: 350,img:'https://pa1.narvii.com/5999/831c04cee5973592fd427841a4e45d9d78e49cf2_hq.gif',img1:'https://animatedit.files.wordpress.com/2016/03/narutoc200.gif?w=723',img2:'https://cdn2.scratch.mit.edu/get_image/gallery/27141030_200x130.png'},
                  ],
        monter : [{name: 'Darth Vader',hp: 300,img:'https://purepng.com/public/uploads/medium/purepng.com-darth-vaderdarth-vaderanakin-skywalkerstar-wars-franchiseskywalker-1701527754593nlxbt.png',},
                  {name: 'Dio',hp: 330,img:'https://i.pinimg.com/originals/17/1d/7a/171d7ab12e92c88fbe4602e816b5c041.png'},
                  {name: 'Thanos',hp: 400,img:'https://2.bp.blogspot.com/-Y4D3zyo2ETY/Wt-LXPf4WxI/AAAAAAAABWQ/TdYzOr3fdioqDgyo6lq-uXe7wfuhgP1swCLcBGAs/s1600/Thanos%2B10.gif?fbclid=IwAR2WrghEacxIWipfIMql0fiky9Nifu14CxmB7PqsOcNGOXinQZWdDIpZd0Q'},
                  {name: 'Dr.Octavius',hp: 300,img:'https://cdn.discordapp.com/attachments/709406382134263882/745701419905974412/pngegg_20.png'},
                   ],
        selecimg: null, 
        ppower : '',
        mhp : '-1',
        mpower: '',
        php : '-1',
        p : 0,
        m : 0,
        end : false,
        animation:0,
      }
 },
    methods: {
   create : function(php,mhp){
       this.php = this.player[php].hp;
       this.mhp = this.monter[mhp].hp;
       this.ppower = 0;
       this.mpower = 0;
       this.end= false;
       this.animation=0;
   },
    random: function () {
      this.ppower = Math.floor(Math.random() * 8 + 3);
      this.mhp = this.mhp - this.ppower;
      this.mpower = Math.floor(Math.random() * 11 + 5);
      this.php = this.php - this.mpower;
      this.animation = 1;
    },
    srandom: function () {
      this.ppower = Math.floor(Math.random() * 11 + 10);
      this.mhp = this.mhp - this.ppower;
      this.mpower = Math.floor(Math.random() * 11 + 5);
      this.php = this.php - this.mpower;
      this.animation = 2;
    }, 
    randomC: function(min, max) { 
     this.p =  Math.floor(Math.random() *(max + 1 )) + min
     this.m =  Math.floor(Math.random() *(max + 1 )) + min  
     },  
    check: function(){
      if (this.php <= 0) {
        this.php = 0;
        this.end = true;
        this.mhp= 500

      } else if (this.mhp <= 0) {
        this.mhp = 0;
        this.end = true;
        this.php= 500;
        this.animation = 0;
      }

    },
}
}
</script>
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style >
</style>
