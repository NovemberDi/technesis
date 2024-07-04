<template>
  <v-app>
    <div class="content">
      <ListOfTags class="content__item1" :tags="listOfTags" alignment="width" />
      <ListOfTags class="content__item2" :tags="listOfTags" alignment="left" />
      <ListOfTags class="content__item3" :tags="listOfTags" alignment="width" />
      <ListOfTags class="content__item4" :tags="listOfTags" alignment="left" />
    </div>
  </v-app>
</template>

<script>
import ListOfTags from './components/ListOfTags';

export default {
  name: 'App',

  components: {
    ListOfTags
  },
  data() {
    return {
      listOfTags: [
        {
          text: 'Тег первый',
          icon: 'mdi-message-text'
        },
        {
          text: 'Тег второй',
          icon: 'mdi-dialpad'
        },
        {
          text: 'Тег номер три',
          icon: 'mdi-ab-testing'
        },
        {
          text: 'Ещё тег',
          icon: 'mdi-account'
        },
        {
          text: 'И тег номер 5',
          icon: 'mdi-medal-outline'
        },
      ]
    }
  }
}
</script>
<style scoped lang="scss">
.content {
  position: relative;
  width: 100%;
  display: block;

  & .content__item1 {
  height: 70px;
  position: relative;
}

& .content__item2 {
  height: 70px;
  position: relative;
}

& .content__item3 {
  width: 50%;
  height: 70px;
  position: relative;
}

& .content__item4 {
  width: 50%;
  height: 70px;
  position: relative;
}

}


</style>
