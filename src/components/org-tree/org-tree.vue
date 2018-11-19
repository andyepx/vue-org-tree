<template>
  <div class="org-tree-container">
    <div class="org-tree" :class="{horizontal, collapsible}">
      <org-tree-node
        :data="data"
        :props="props"
        :horizontal="horizontal"
        :label-width="labelWidth"
        :collapsible="collapsible"
        :render-content="renderContent"
        :label-class-name="labelClassName"
        @on-expand="$emit('on-expand', $event)"
        @on-node-click="(e, data) => {$emit('on-node-click', e, data)}"
      ></org-tree-node>
    </div>
  </div>
</template>

<script>
  import render from './node'

  export default {
    name: 'Vue2OrgTree',
    components: {
      OrgTreeNode: {
        render,
        functional: true
      }
    },
    props: {
      data: {
        type: Object,
        required: true
      },
      props: {
        type: Object,
        default: () => ({
          label: 'label',
          expand: 'expand',
          children: 'children'
        })
      },
      horizontal: Boolean,
      collapsible: Boolean,
      renderContent: Function,
      labelWidth: [String, Number],
      labelClassName: [Function, String]
    }
  }
</script>

<style lang="less">
  @import '../../styles/org-tree';
</style>
