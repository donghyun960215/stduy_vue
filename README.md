# VUE

## vue 간단하게 파악하기
```html
<!--Template 부분은 HTML(vue)-->
<template>
  <!--@click = 클릭이 될 때 마다 increase() 실행-->
  <h1 @click="increase">
    {{ count }}
  </h1>
</template>

<!--Script 부분은 js(vue)-->
<script>
export default {
  data() {
    return{
      count: 0
    }
  },
  methods: {
    //increase() 실행이 될때 마다 count +1 씩해준다
    increase() {
      this.count += 1
    }
  }
}
</script>

<!--style 부분은 css(scss)-->
<style>
  h1{
    font-size: 50px;
    color: red;
  }
</style>
```
```plaintext
상단내용은 간단한 vue내용이다. script에서 count를 만들어 주고 increase()매소드가 실행이 될 때 마다 count +1 이 된다
그리고 template에서 count를 표출해주고 @click 를 이용해서 클릭이 될 때 마다 매소드가 실행이 된다. 
그러면 화면에서 클릭을 할 떄 마다 +1 된다.
```
## scss 적용
```html
<template>
</template>

<script>
</script>

<style scoped lang = "scss">
  h1{
    font-size: 50px;
    color: red;
  }
  ul {
    li{
      font-size: 40px;
    }
  }
</style>
```
```plaintext
 css가아닌 scss를 사용하고 싶으면 lang="scss" 를 추가한다.
 scoped는 해당하는 vue파일에 작성한 내용 말고는 다른 파일에는 적용이 안된다.(components 해도 소용 없다.)
```

## 간단한 if문
```html
<template>
  <h1 @click="increase">
    {{ count }}
  </h1>
  <div v-if="count > 4">
    4보다 큽니다.
  </div>
</template>

<script>
export default {
  data() {
    return{
      count: 0
    }
  },
  methods: {
    increase() {
      this.count += 1
    }
  }
}
</script>

<style>
  h1{
    font-size: 50px;
    color: red;
  }
</style>
```
```plaintext
상단의 내용은 간단한 if문이다.
<div v-if="count > 4">
    4보다 큽니다.
</div>
내용을 해석하면 초기 화면에는 글의 내용이 보이지 않고 count가 4보다 크게되면 그 때 화면에서 나오게 된다.
즉 클릭을 5번을 해야지 해당 글의 내용이 나오게된다.
```

## 간단한 for 문
```html
<template>
  <ul>
    <!--
      script에 있는 fruits배열 데이터를 template에 있는 fruits 에 저장한다.
      배열데이터의 갯수만큼 3번 반복한다.
      그리고 그 부분을 fruit에 넣고 데이터로서 활용을 한다.
      key 부분은 값이 고유하다라는 증명이다.
    -->
    <li
      v-for="fruit in fruits"
      :key="fruit">
      {{ fruit }}
    </li>
  </ul>
</template>

<script>
export default {
  data() {
    return{
      //fruits라는 배열데이터를 생성했다.
      fruits: ['Apple','Banana','cherry']
    }
  }
}
</script>

<style>
  h1{
    font-size: 50px;
    color: red;
  }
  ul {
    li{
      font-size: 40px;
    }
  }
</style>
```
```palintext
상단의 내용은 간단한 for문 내용이다. 
script 에서 fruits 라는 배열 데이터를 생성해주고
template 부분의 fruits에 저장한다. 배열아이템이 총 3개 있으므로 3번 반복한다.
그리고 fruits를 fruit의 담아서 화면에 표현한다.
key 값은 데이터가 고유하다라고 보여주는 부분이다.
```

## components
```html
<!--
  component 파일 내용

  <template>
  <li>{{ name }}</li>
</template>

<script>
export default {
  props: {
    name: {
      type: String,
      default: ''
    }
  }
}
</script>

<style>

</style>
-->
<template>
  <ul>
    <hello
      v-for="fruit in fruits"
      :key="fruit">
      {{ fruit }}
    </hello>
  </ul>
</template>

<script>
import Fruit from '~/components/Fruit';

export default {
  components: {
    hello: Fruit
  },
  data() {
    return{
      fruits: ['Apple','Banana','cherry']
    }
  }
}
</script>

<style lang = "scss">
  h1{
    font-size: 50px;
    color: red;
  }
  ul {
    li{
      font-size: 40px;
    }
  }
</style>
```
```plaintext
1.components 폴더에 component할 파일을 생성하고 조건에 맞게 입력한다.
2.그 후 연결할 파일에 script 부분에 import 한다.
    <script>
    import Fruit from '~/components/Fruit';

    export default {
      components: {
        hello: Fruit
      }
    }
    </script>
3. import 한 후 components함수를 사용해서 hello에 Fruit내용을 넣어준다.
4. 상단에 ul태그 안에 있는 hello 처럼 사용을 한다.
5. name="fruit" 지정하여 데이터를 넣어준다.

```
