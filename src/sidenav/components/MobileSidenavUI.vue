<template>
  <div>
    <SidenavBox
      v-if="currentUserId"
      :expandable="false"
    >
      <template slot="icon">
        <q-icon name="fas fa-fw fa-user-circle" />
      </template>

      <template slot="name">
        {{ $t('USERDATA.ACCOUNT') }}
      </template>

      <q-list
        no-border
        link
      >
        <q-item
          item
          :to="{name: 'user', params: {userId: currentUserId}}"
        >
          <q-item-side>
            <i class="fas fa-user fa-fw"/>
          </q-item-side>
          <q-item-main :label="$t('TOPBAR.USERPROFILE')" />
        </q-item>

        <q-item
          item
          :to="{name: 'groupsGallery'}"
        >
          <q-item-side>
            <i class="fas fa-exchange-alt"/>
          </q-item-side>
          <q-item-main :label="$t('TOPBAR.CHANGE_GROUP')" />
        </q-item>

        <q-item
          item
          :to="{name: 'settings'}"
        >
          <q-item-side>
            <i class="fas fa-cog fa-fw"/>
          </q-item-side>
          <q-item-main :label="$t('SETTINGS.TITLE')" />
        </q-item>

        <q-item
          @click.native="$emit('logout'), $emit('toggleSidenav')"
        >
          <q-item-side>
            <i class="fas fa-sign-out-alt fa-fw"/>
          </q-item-side>
          <q-item-main :label="$t('TOPBAR.LOGOUT')" />
        </q-item>
      </q-list>
    </SidenavBox>
    <SidenavBox :expandable="false">
      <template slot="icon">
        <q-icon name="fas fa-info-circle" />
      </template>

      <template slot="name">
        Info
      </template>

      <q-list
        no-border
        link
      >
        <q-item
          link
          tag="a"
          rel="nofollow noopener noreferrer"
          href="https://community.foodsaving.world"
        >
          <q-item-side>
            <i class="fas fa-users"/>
          </q-item-side>
          <q-item-main
            label="Community"
            :sublabel="$t('GLOBAL.COMMUNITY_NOTE')"
          />
        </q-item>

        <q-item
          link
          tag="a"
          rel="nofollow noopener noreferrer"
          href="https://foodsaving.world"
        >
          <q-item-side>
            <i class="fas fa-paint-roller"/>
          </q-item-side>
          <q-item-main
            label="Info"
            :sublabel="$t('SIDENAV.INFO_SUB')"
          />
        </q-item>

        <q-item
          link
          tag="a"
          rel="nofollow noopener noreferrer"
          href="https://blog.karrot.world"
        >
          <q-item-side>
            <i class="far fa-newspaper"/>
          </q-item-side>
          <q-item-main
            label="Blog"
            :sublabel="$t('SIDENAV.BLOG_SUB')"
          />
        </q-item>

        <q-item
          link
          tag="a"
          rel="nofollow noopener noreferrer"
          href="https://github.com/yunity/karrot-frontend"
        >
          <q-item-side>
            <i class="fab fa-git"/>
          </q-item-side>
          <q-item-main
            label="Git"
            :sublabel="$t('SIDENAV.GIT_SUB')"
          />
        </q-item>
      </q-list>
    </SidenavBox>
  </div>
</template>
<script>

import {
  QList,
  QListHeader,
  QIcon,
  QItem,
  QItemSeparator,
  QItemSide,
  QItemMain,
} from 'quasar'
import SidenavBox from '@/sidenav/components/SidenavBox'

export default {
  components: {
    QList,
    QListHeader,
    QIcon,
    QItem,
    QItemSeparator,
    QItemSide,
    QItemMain,
    SidenavBox,
  },
  props: {
    currentUserId: {
      type: Number | null,
      default: null,
    },
  },
}
</script>
