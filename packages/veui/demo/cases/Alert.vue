<template>
<article>
  <h1>
    <code>&lt;veui-alert&gt;</code>
  </h1>
  <section>
    <div>固定提示</div>
    <veui-alert
      status="success"
      ui="strong"
      message="恭喜你，你的请求已成功处理"
      closable
    >
      <template #title>恭喜你</template>
      <template #extra>
        <veui-button ui="text">查看详情</veui-button>
      </template>
      恭喜你，你的请求已成功处理
    </veui-alert>
    <veui-alert
      status="success"
      ui="s"
      message="恭喜你，你的请求已成功处理"
      closable
      :show-icon="false"
    >
      <template #title>恭喜你</template>
      恭喜你，你的请求已成功处理，欢迎
      <a href="#" ui="strong">查看详情</a>。
    </veui-alert>
    <veui-alert
      status="success"
      message="恭喜你，你的请求已成功处理"
      closable
      ui="m strong"
    >
      <template #title>恭喜你</template>
      <template #extra>
        <veui-button ui="text">查看详情</veui-button>
      </template>
      恭喜你，你的请求已成功处理
    </veui-alert>
    <veui-alert
      class="limit-width"
      ui="strong s"
      status="success"
      message="恭喜你，你的请求已成功处理 恭喜你，你的请求已成功处理 恭喜你，你的请求已成功处理 恭喜你，你的请求已成功处理 恭喜你，你的请求已成功处理 恭喜你，你的请求已成功处理 恭喜你，你的请求已成功处理 恭喜你，你的请求已成功处理 恭喜你，你的请求已成功处理 恭喜你，你的请求已成功处理 恭喜你，你的请求已成功处理 恭喜你，你的请求已成功处理 恭喜你，你的请求已成功处理 恭喜你，你的请求已成功处理 恭喜你，你的请求已成功处理"
      closable
    />
    <veui-alert
      status="warning"
      ui="strong"
      message="警告，进行检查，有风险信息存在"
    />
    <veui-alert
      class="limit-width"
      status="warning"
      ui="s"
      :message="messages"
      closable
    />
    <veui-alert
      class="limit-width"
      status="warning"
      :message="messages"
      closable
    >
      <template #extra="{ message }">
        <veui-button ui="text">查看详情 {{ message }}</veui-button>
      </template>
    </veui-alert>
    <veui-alert status="info" ui="s" message="提醒，这个消息需要注意"/>
    <veui-alert
      class="limit-width"
      status="info"
      message="提醒，这个消息需要注意"
      close-label="不再提示"
    />
    <veui-alert
      status="error"
      ui="s"
      message="错误，请检查并修改后再进行操作"
    />
    <veui-alert
      class="limit-width"
      status="error"
      message="错误，请检查并修改后再进行操作"
    />
  </section>
</article>
</template>

<script>
import bus from '../bus'
import { Alert, Button } from 'veui'

export default {
  name: 'alert-demo',
  components: {
    'veui-alert': Alert,
    'veui-button': Button
  },
  data () {
    return {
      open: false,
      messages: [
        '我是消息1我是消息1我是消息1我是消息1',
        '我是消息2',
        '我是消息3',
        '我是消息4',
        '我是消息5'
      ],
      messageIndex: 0
    }
  },
  mounted () {
    this.$children.forEach((child) => {
      child.$on('click', () => {
        bus.$emit('log', child.$el.getAttribute('ui'))
      })
    })
  },
  methods: {
    close () {
      this.open = true
    }
  }
}
</script>

<style scoped>
section {
  margin: 30px;
}

.veui-alert {
  margin: 30px 0;
}

.veui-alert.limit-width {
  width: 650px;
}
</style>
