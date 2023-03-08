<template>
  <div class="story"></div>

  <div v-for="(p,i) in posts" :key="i" class="post">
    <div class="top" style="font-size: 25px">
      <span class="profile__pic"><i class="fa-solid fa-circle"></i></span>
      <span class="profile__id">  tarisko</span>
    </div>

    <div class="middle">
      <img :src="p.imgSrc" />
    </div>

    <div class="bottom">
      <div class="button">
        <ul class="right">
          <li @click="toggleLike(p)" v-if="!p.like" class="likeBtn"><i class="fa-regular fa-heart"></i></li>
          <li @click="toggleLike(p)" v-if="p.like" class="likeBtn"><i class="fa-solid fa-heart"></i></li>
          <li class="commentBtn"><i class="fa-regular fa-comment"></i></li>
          <li class="dmBtn"><i class="fa-regular fa-paper-plane"></i></li>
        </ul>
        <div class="bookmark">
          <div @click="toggleBookmark(p)" class="bookmarkBtn" v-if="!p.bookmarked"><i class="fa-regular fa-bookmark"></i></div>
          <div @click="toggleBookmark(p)" class="bookmarkBtn" v-if="p.bookmarked"><i class="fa-solid fa-bookmark"></i></div>
        </div>
      </div>
      <div class="post__info">
        <p style="font-weight: bold;">좋아요 {{ p.liked }}개</p>
        <span style="font-weight: bold">{{ p.userId }}</span> {{ p.posting }}
        <p style="color: gray">댓글 {{ p.comments.length }}개 보기</p>
        <p style="color: gray; font-size: 12px">{{ p.posted_date }}</p>
        <p>댓글창</p>
        

      </div>
    </div>
  </div>
</template>

<script>
export default {
  data(){
    return{
      posts:[{
        imgSrc: 'https://mblogthumb-phinf.pstatic.net/MjAxOTEyMzFfMTQ5/MDAxNTc3NzgyMzAxODMy.SOVYp_FhVqX0uIy36sG4rNG8-nMwkmvHRYLi2ZCUkvQg.EUcGanMQ8n4PMOL83OFG5za8gbNtB3jzggRsnJXp0Q4g.JPEG.kugsh229/0c6124303e443dc1c906751f1361cc04.jpg?type=w800',
        userId: 'tarisko',
        liked: 3,
        posted_date: '1일전',
        posting: '첫번째 게시물',
        comments: ['1st comments', '두번째 댓글', '3333333'],
        bookmarked: false,
        like: false,

      },{
        imgSrc: 'data:image/jpeg;base64,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',
        userId: 'tarisko',
        liked: 7,
        posted_date: '2023-02-14',
        posting: '2일전',
        comments: ['1st comments', '두번째 댓글', '3333333'],
        bookmarked: false,
        like: false,
      }]
    }
  }, methods:{
    toggleBookmark(spost){
      spost.bookmarked = !spost.bookmarked
    },
    toggleLike(spost){
      spost.like = !spost.like
    }
      
    }

    
}


</script>

<style>
.story{
  display: inline-block;
  margin-top: 30px;
  margin-left: 450px;
  width: 512px;
  height: 100px;
  border: 0.1px rgb(68, 68, 68) solid;
  border-radius: 10px;

}


.post{
  display: inline-block;
  margin-top: 30px;
  margin-left: 450px;
  width: 512px;
  border: 0.1px rgb(68, 68, 68) solid;
  border-radius: 10px;
}
.top{
  display: block;
  box-sizing: border-box;
  /* border: 1px white solid; */
  height: 50px;
  padding: 7px;
}

.middle{
  box-sizing: border-box;
  /* border: 1px white solid; */
  
}
.middle img{
  display: block;
  width: 100%;
  /* padding: 0; */
}
.bottom{
  box-sizing: border-box;
  /* border: 1px white solid; */
  /* margin: 0; */

}
.button{
  font-size: 20px;
  display: flex;
  justify-content: space-between;
}
.right{
  list-style: none;
  padding: 0;
  margin: 0;
}
.right li{
  float: left;
}
.likeBtn{
  cursor: pointer;
  margin: 10px;
}
.commentBtn{
  cursor: pointer;
  margin: 10px;
}
.bookmarkBtn{
  display: block;
  cursor: pointer;
  margin: 10px;
  /* font-size: 40px; */
}
.dmBtn{
  cursor: pointer;
  margin: 10px;
}
.post__info{
  margin: 10px;
}
</style>