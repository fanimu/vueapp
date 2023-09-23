<script>
export default {
  name: 'NotificationPage',
  data() {
    return {
      notifs: [
        {
          name: 'Mark Webber',
          avatar: 'jacob-thompson',
          action: 'reacted',
          time: '1m ago',
          hasRead: true,
        },
        {
          name: 'Angela Gray',
          avatar: 'angela-gray',
          action: 'follow',
          time: '5m ago',
          hasRead: true,
        },
        {
          name: 'Jacob Thompson',
          avatar: 'jacob-thompson',
          action: 'join',
          time: '1day ago',
          hasRead: true,
        },
        {
          name: 'Rizky Hasanuddin',
          avatar: 'rizky-hasanuddin',
          action: 'message',
          time: '5 days ago',
          message: "Hello, thanks for setting up the Chese Club. I've been a member for a few weeks now and I'm already having lots of fun and improving my game.",
          hasRead: false,
        },
        {
          name: 'Kimberly Smith',
          avatar: 'kimberly-smith',
          action: 'comment',
          time: '1week ago',
          hasRead: false,
        },
        {
          name: 'Nathan Peterson',
          avatar: 'nathan-peterson',
          action: 'reacted',
          time: '2 weeks ago',
          hasRead: false,
        },
        {
          name: 'Anna Kim',
          avatar: 'anna-kim',
          action: 'left',
          time: '2 weeks ago',
          hasRead: false,
        },
      ],
    };
  },
};
</script>

<template>
  <div class="w-screen flex overflow-auto">
    <div class="w-6/12 h- mx-auto h-auto bg-white shadow-lg px-12 py-10">
      <!-- header -->
      <div class="flex justify-between mb-6 items-end">
        <div class="flex gap-1 items-center">
          <h1 class="font-bold text-lg">Notification</h1>
          <span class="px-2 bg-blue-900 text-white font-semibold rounded-md text-center">3</span>
        </div>
        <span class="text-sm text-gray-500">Mark all as read</span>
      </div>

      <!-- content -->
      <div v-for="(notif, index) in notifs" :key="index" class="p-4 bg-slate-100 rounded-md mb-4">
        <!-- container notif -->
        <div class="flex gap-4 items-start">
          <!-- avatar -->
          <!-- TODO: CHANGE TO BASE64 -->
          <img :src="require(`../assets/images/avatar-${notif.avatar}.webp`)" alt="avatar thumbnail" class="w-10" />
          <!-- text -->
          <div class="text-sm">
            <div>
              <p v-if="notif.action === 'join'">
                <b>{{ notif.name }}</b> has join your group <b class="text-gray-300">Chese Club</b>
              </p>
              <p v-else-if="notif.action === 'follow'">
                <b>{{ notif.name }}</b> followed you
              </p>
              <p v-else-if="notif.action === 'reacted'">
                <b>{{ notif.name }}</b> reacted to your recent post
                <b v-if="notif.name === 'Mark Webber'" class="text-gray-300">My first tournament today!</b>
                <span v-if="notif.name === 'Nathan Peterson'" class="text-black text-sm font-bold text-gray-600">5 end-game strategis to increase your win rate</span>
              </p>
              <p v-else-if="notif.action === 'comment'">
                <b>{{ notif.name }}</b> commented on your picture
              </p>
              <p v-else-if="notif.action === 'left'">
                <b>{{ notif.name }}</b> left the group <b class="text-blue">Chese Club</b>
              </p>
              <p v-else>
                <b>{{ notif.name }}</b> sent you a private message
              </p>

              <span class="text-gray-500 text-sm cursor-pointer">{{ notif.time }}</span>
            </div>

            <div v-if="notif.action === 'message'" class="border-2 border-gray-200 p-2 rounded-md">
              <p class="text-gray-700">{{ notif.message }}</p>
            </div>
          </div>
          <div v-if="notif.hasRead === true" class="mt-2 w-3 h-3 rounded-full bg-red-500"></div>
          <div v-if="notif.action === 'comment'">
            <img src="../assets/images/image-chess.webp" class="w-10 rounded-full" alt="" />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
