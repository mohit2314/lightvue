<template>
  <docs-page-layout :title="$options.title" :description="$options.description" :status="$options.status">
    <docs-card-vue title="Dialog" file="dialog/DialogDemo" />
    <template #api>
      <getting-started :package-name="$options.packageName" :component-name="$options.componentName" />
      <docs-all-api :api-data="$options.apiData" />
    </template>
  </docs-page-layout>
</template>

<script>
import DocsPageLayout from '@/components/docs-card/DocsPageLayout';
import DocsCardVue from '@/components/docs-card/DocsCardVue';
import DocsCard from '@/components/docs-card/DocsCard';
import GettingStarted from '@/components/docs-card/GettingStarted';
import DocsAllApi from '@/components/docs-card/DocsAllApi';
import DialogAPI from 'lightvueDocs/example/dialog/DialogAPI';
import { COMPONENT_STATUS } from '@/static/data/constant.ts';

export default {
  head: {
    title: ' Dialog Documentation | LightVue ',
    meta: [
      { charset: 'utf-8' },
      { name: 'viewport', content: 'width=device-width, initial-scale=1' },
      { property: 'og:title', content: 'LightVue' },
      { property: 'og:image', content: 'https://lightvue.com/icon.png' },
      {
        property: 'og:site_name',
        content: ' Dialog Documentation | LightVue ',
      },
      {
        property: 'og:description',
        content: 'LightVue Dialog helps the user to have modal and additional dialog box with their data.',
      },
    ],
    link: [{ rel: 'icon', type: 'image/x-icon', href: '/favicon.ico' }],
  },
  components: {
    DocsCardVue,
    DocsCard,
    GettingStarted,
    DocsPageLayout,
    DocsAllApi,
  },
  title: 'Dialog',
  description: `Lv Dialog helps the user to have modal and additional dialog box with their data.`,
  packageName: 'dialog',
  componentName: 'LvDialog',
  status: COMPONENT_STATUS.UNDER_DEVELOPMENT,
  apiData: DialogAPI,
};
</script>
