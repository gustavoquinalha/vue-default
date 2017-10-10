# [Monk placeholder content](https://monk-placeholder-content.herokuapp.com/)

![GIF](https://github.com/gustavoquinalha/monk-placeholder-content-docs/blob/master/src/assets/images/gif1.gif)

[See docs](https://monk-placeholder-content.herokuapp.com/)

## Get started

```
$ npm i monk-placeholder-content -D
```

- Criar a variavel de carregamento, nesse exemplo usaremos 'loading', defina como true
- Na div principal adicione v-show="!loading"
- no component adicione v-show="loading"
- Na requisicao da chamada. loading é true, quando recebe os dados loading é false

```html
<template>
  <div>
    <div v-show="loading">
      <placeholderContent type="card" :photo="true" :title="false" :description="true" :number="2" :button="false" :head="false" v-for="x in 5"></placeholderContent>
    </div>
    <div v-show="!loading">
      Loaded
    </div>
  </div>
</template>
```
```javascript
export default {
    data () {
      return {
        loading: 'true',
    },
    methods: {
       search: function (txt) {
        this.isLoading = true
        this.$http.get('/youtube/music', {
          params: {
            search: txt
          }
        })
        .then(
          response => {
            this.isLoading = false
            console.log(response)
            this.videos = response.body
            this.txt = ''
          })
        .catch(
          error => {
            this.isLoading = false
            console.log('Error' + JSON.stringify(error))
          })
      },
    }
  }
}
```
