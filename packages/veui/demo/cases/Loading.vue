<template>
<article>
  <h1>
    <code>&lt;veui-loading&gt;</code>
  </h1>
  <div class="veui-loading-demo">
    <section>
      <h3>基础加载</h3>
      <p>
        大尺寸：
        <veui-loading loading ui="l"/>
      </p>
      <p>
        中等尺寸：
        <veui-loading loading ui="m"/>
      </p>
      <p>
        小尺寸：
        <veui-loading loading ui="s"/>
      </p>
      <p>
        普通效果：
        <veui-loading loading ui="normal"/>
      </p>
      <p>
        加强效果：
        <veui-loading loading ui="strong"/>
      </p>
      <p>
        反白效果：
        <veui-loading loading ui="reverse" class="reverse"/>
      </p>
    </section>
    <section>
      <h3>含辅助文案加载</h3>
      <p>
        大尺寸：
        <veui-loading loading ui="l">加载中...</veui-loading>
      </p>
      <p>
        中等尺寸：
        <veui-loading loading ui="m">加载中...</veui-loading>
      </p>
      <p>
        小尺寸：
        <veui-loading loading ui="s">加载中...</veui-loading>
      </p>
      <p>
        普通效果：
        <veui-loading loading ui="normal">加载中...</veui-loading>
      </p>
      <p>
        加强效果：
        <veui-loading loading ui="strong">加载中...</veui-loading>
      </p>
      <p>
        反白效果：
        <veui-loading
          loading
          ui="reverse"
          class="reverse"
        >加载中...</veui-loading>
      </p>
      <p>
        文字垂直显示：
        <veui-loading
          loading
          class="reverse"
          ui="reverse vertical"
        >加载中...</veui-loading>
      </p>
    </section>
    <section>
      <h3>自定义加载图标</h3>
      <p>
        自定义图标-星星：
        <veui-loading loading ui="strong">
          <template #spinner>
            <veui-icon spin name="star"/>
          </template>
          拼命加载中...
        </veui-loading>
      </p>
      <p>
        自定义图标-太阳：
        <veui-loading loading>
          <template #spinner>
            <veui-icon spin name="clockwise"/>
          </template>
          拼命加载中...
        </veui-loading>
      </p>
      <p>
        自定义图标-雨伞：
        <veui-loading loading ui="reverse" class="reverse">
          <template #spinner>
            <veui-icon spin name="loading"/>
          </template>
          拼命加载中...
        </veui-loading>
      </p>
    </section>
    <section>
      <h3>简单示例</h3>
      <p>
        MVP选票数：
        <veui-loading :loading="loading">实时MVP选票数加载中...</veui-loading>
        <template v-if="!loading">
          <veui-span>{{ voteAccount }}</veui-span>
          <veui-button
            ui="primary"
            @click="handleClick"
          >获取实时投票数</veui-button>
        </template>
      </p>
    </section>
    <section>
      <h3>遮罩层展现</h3>
      <section class="cards">
        <div class="card">
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Voluptate
          similique nam, iure maiores consequatur quia suscipit temporibus
          corporis ipsa molestias magnam repudiandae. Nam nihil eveniet eius
          dolores ducimus cumque facere.
          <veui-loading loading ui="strong l overlay">正在加载…</veui-loading>
        </div>
        <div class="card">
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Voluptate
          similique nam, iure maiores consequatur quia suscipit temporibus
          corporis ipsa molestias magnam repudiandae. Nam nihil eveniet eius
          dolores ducimus cumque facere.
          <veui-loading loading ui="reverse l overlay"/>
        </div>
      </section>
    </section>
  </div>
</article>
</template>
<script>
import 'veui-theme-dls-icons/star'
import 'veui-theme-dls-icons/clockwise'
import 'veui-theme-dls-icons/loading'

import { Loading, Button, Icon, Span } from 'veui'
export default {
  name: 'loading',
  components: {
    'veui-loading': Loading,
    'veui-button': Button,
    'veui-icon': Icon,
    'veui-span': Span
  },
  data () {
    return {
      loading: false,
      voteAccount: 120
    }
  },
  methods: {
    handleClick () {
      this.loading = true
      setTimeout(() => {
        this.loading = false
        this.voteAccount += 100
      }, 1000)
    }
  }
}
</script>
<style lang="less">
.veui-loading-demo {
  .reverse {
    background: #ccc;
    padding: 8px;
  }

  p {
    display: flex;
    line-height: 32px;
  }

  .veui-span {
    margin-right: 15px;
  }

  .cards {
    display: flex;
  }

  .card {
    position: relative;
    width: 320px;
    height: 180px;
    margin-right: 20px;
    padding: 1em 1.5em;
    line-height: 1.6;
    border: 1px solid #ccc;
    border-radius: 4px;
    box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
  }
}
</style>
