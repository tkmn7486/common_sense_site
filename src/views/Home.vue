<template>
  <div class="home">
    <div class="recommend_cont" :style="{display:reco_cont_view}">
      <h3 class="recommend_title">>>おすすめ</h3>
      <div class="list_contents">
        <div class="content_border" v-for="reco_cont in reco_list" :key="reco_cont.id" @click="open_artic(reco_cont)">
          <div class="content">
            <h4 class="content_title">{{reco_cont.title}}</h4>
            <div class="tags">
              <div class="tag_list" v-for="tags in reco_cont.tag" :key="tags.id">
                <button class="tag_button" @click="search_from_tag">{{tags}}</button>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
    <!-- 記事表示画面 -->
    <div class="article_space">
      <h2>{{artic_title}}</h2>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import {ref} from 'vue'

export default {
  name: 'Home',
  setup(){
    let reco_list = ref([
      {id:0, title:"お焼香の作法", comment:"仏式葬儀のお焼香作法について", tag:["葬儀","作法","仏教"]},
      {id:1, title:"確定申告とは", comment:"確定申告って何？という方のための要約", tag:["税金","年末","副業"]},
      {id:2, title:"年末調整とは", comment:"年末調整って何？という方のための要約", tag:["税金","年末","副業"]},
    ])

    let reco_cont_view = ref("block");

    let contents = ref(0)

    let cont_data = ref([])

// 記事画面の要素
    let artic_title = ref()
    let artic_date =ref()
    let artic_sentence = ref()

    const open_artic=(name)=>{
      prepare_artic(name);
      change_view(reco_cont_view, "none", "block");
    }

    const prepare_artic=(name)=>{
      artic_title.value = name.title
      console.log(artic_title.value);
      get_contents(name.value.date,artic_date);
      get_contents(name.value.sentense,artic_sentence);
      // artic_date.value = name.value.date
      // artic_sentence.value = name.value.sentence
    }

    const get_contents=(cont, artic)=>{
      if(cont){
        artic.value = cont;
      }else{
        artic.value = ""
      }
    }

    const change_view=(view, style1, style2)=>{
      if(view.value == style1){
        view.value = style2;
      }else{
        view.value = style1;
      }
    }

    return{
      reco_list,
      cont_data,
      contents,
      artic_title,
      artic_date,
      artic_sentence,

      // 表示管理変数
      reco_cont_view,

      prepare_artic,
      open_artic,
      change_view,
      get_contents,
    }
  }

}
</script>

<style>
  .reco_cont_view{
    display:none;
  }

  .recommend_title{
    margin:10px;
    border-bottom:double 5px;
    width:130px;
  }

  .content_border{
    border:solid 1px;
    border-radius:10px;
    margin:10px;
    width:30%;
    display:inline-block;
    box-shadow: 0 10px 15px 0 rgba(0, 0, 0, .5);
  }

  .content{
    text-align:center;
    padding:20px;
  }

  .content_title{
    margin:5px 0 0 5px;
  }

  .content_comment{
    margin:5px 0 0 5px;
  }

  .tags{
    margin-top:10px;
  }

  .tag_button{
    border:solid 1px;
    border-radius:5px;
    background-color:white;
    font-size:5px;
    text-align:center;
    padding:0 3px 0 3px;
    margin:0 3px 0 3px;
  }

  .tag_list{
    display:inline-block;
  }

/* スマホ用CSS */
@media screen and (max-width:480px) {

  .recommend_title{
    margin:10px;
    border-bottom:double 5px;
    width:130px;
  }

  .content_border{
    border:solid 1px;
    border-radius:10px;
    width:40%;
    display:inline-block;
    box-shadow: 0 10px 15px 0 rgba(0, 0, 0, .5);
  }

  .content{
    text-align:center;
    padding:20px;
  }

  .content_title{
    font-size:15px;
    margin:5px 0 0 5px;
  }

  .content_comment{
    margin:5px 0 0 5px;
  }

  .tags{
    margin-top:10px;
  }

  .tag_button{
    border:solid 1px black;
    border-radius:5px;
    background-color:#ffffff;
    font-size:80%;
    text-align:center;
    padding:0 3px 0 3px;
    margin:0 3px 0 3px;
  }

  .tag_list{
    display:inline-block;
  }

}

</style>