<template>
  <div id="editor">
    <nav>
      <ol>
        <li v-for="i in [0, 1, 2, 3, 4, 5]" v-bind:class="{active: currentTab === i}" v-on:click="currentTab = i">
          <svg class="icon" aria-hidden="true">
            <use v-bind:xlink:href="`#icon-${icons[i]}`"></use>
          </svg>
        </li>
      </ol>
    </nav>
    <ol class="panes">
      <li v-bind:class="{active: currentTab === 0}">
        <ProfileEditor v-bind:profile="profile"/>
      </li>
      <li v-bind:class="{active: currentTab === 1}">
        <ArrayEditor v-bind:items="workHistory" v-bind:labels="{company: '公司', content: '工作内容' }" title="工作经历"/>
      </li>
      <li v-bind:class="{active: currentTab === 2}">
        <ArrayEditor v-bind:items="studyHistory" v-bind:labels="{school: '学校', duration: '时间', degree: '学位'}" title="学习经历"/>
      </li>
      <li v-bind:class="{active: currentTab === 3}">
        <ArrayEditor v-bind:items="projects" v-bind:labels="{name: '项目名称', duration: '工作内容'}" title="项目经历"/>
      </li>
      <li v-bind:class="{active: currentTab === 4}">
        <ArrayEditor v-bind:items="awards" v-bind:labels="{name: '奖励详情'}" title="获奖情况"/>
      </li>
      <li v-bind:class="{active: currentTab === 5}">
        <ContactsEditor v-bind:contacts="contacts"/>
      </li>
    </ol>
  </div>
</template>

<script>
  import ProfileEditor from './ProfileEditor.vue'
  import ArrayEditor from './ArrayEditor.vue'
  import ContactsEditor from './ContactsEditor.vue'
  export default {
    components: {ProfileEditor, ArrayEditor, ContactsEditor},
    data() {
      return {
        currentTab: 0,
        icons: ['shenfenzheng', 'work', 'book', 'heart', 'jiangbei', '3-copy'],
        profile: {
          name: '', city: '', birth: ''
        },
        workHistory: [
          {company: '', content: ''}
        ],
        studyHistory: [
          {school: '', duration: '', degree: ''}
        ],
        projects: [
          {name: '', content: ''}
        ],
        awards: [
          {name: ''}
        ],
        contacts: {
          qq: '', wechat: '', email: '', phone: ''
        }
      }
    },
    methods: {

    },
    created() {

    }
  }
</script>

<style lang="scss" rel="stylesheet/scss">
  #editor {
    display: flex;
    > nav {
      background-color: #000;
      width: 80px;
      > ol > li {
        padding: 16px 0;
        text-align: center;
        > .icon {
          width: 24px;
          height: 24px;
          fill: #fff;
        }
        &.active {
          background-color: #fff;
          > .icon {
            fill: #000;
          }
        }
      }
    }
    > .panes {
      flex: 1;
      .container {
        position: relative;
        .el-icon-circle-close {
          position: absolute;
          right: 0;
          top: 0;
        }
      }
      > li {
        display: none;
        padding: 32px;
        height: 100%;
        overflow: auto;
        &.active {
          display: block;
        }
      }
    }
  }
</style>
