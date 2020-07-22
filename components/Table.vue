<template>
  <a-table :columns="columns" :data-source="data">
    <a slot="name" slot-scope="text">{{ text }}</a>
    <span slot="customTitle"><a-icon type="smile-o" /> Name</span>
    <span slot="tags" slot-scope="tags">
      <a-tag
        v-for="tag in tags"
        :key="tag"
        :color="tag === 'loser' ? 'volcano' : tag.length > 5 ? 'geekblue' : 'green'"
      >
        {{ tag.toUpperCase() }}
      </a-tag>
    </span>
    <span slot="action" slot-scope="text, record">
      <a>edit</a>
      <a-divider type="vertical" />
      <a>Delete</a>
      <a-divider type="vertical" />
      <a class="ant-dropdown-link"> More actions <a-icon type="down" /> </a>
    </span>
  </a-table>
</template>
<script>
const columns = [
  {
    dataIndex: 'name',
    key: 'name',
    slots: { title: 'customTitle' },
    scopedSlots: { customRender: 'name' },
  },
  {
    title: 'date',
    dataIndex: 'age',
    key: 'age',
  },
  {
    title: 'Address',
    dataIndex: 'address',
    key: 'address',
  },
  {
    title: 'Tags',
    key: 'tags',
    dataIndex: 'tags',
    scopedSlots: { customRender: 'tags' },
  },
  {
    title: 'Action',
    key: 'action',
    scopedSlots: { customRender: 'action' },
  },
];

const data = [
  {
    key: '1',
    name: 'Github',
    age: '2018/6/5',
    address: 'https://github.com/',
    tags: ['前端', '常用'],
  },
  {
    key: '2',
    name: 'vue文档',
    age: '2019/7/9',
    address: 'https://cn.vuejs.org/v2/guide/',
    tags: ['vue'],
  },
  {
    key: '3',
    name: '深入理解Javascrip系列',
    age: '2020/3/7',
    address: 'https://www.cnblogs.com/TomXu/archive/2011/12/15/2288411.html',
    tags: ['javascript', 'teacher'],
  },
];

export default {
  data() {
    return {
      data,
      columns,
    };
  },
};
</script>
