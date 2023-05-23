<template>
  <div class="sidebar">
    <div class="logo">
      <img src="../assets/HubNeroLogoHorisontal.png" alt="" />
    </div>
    <div class="icons">
      <div
        class="icon"
        @click="selectIcon(1)"
        :class="{ active: activeIcon === 1 }"
      >
        <i class="fas fa-home"></i>
      </div>
      <div
        class="icon"
        @click="selectIcon(2)"
        :class="{ active: activeIcon === 2 }"
      >
        <i class="fas fa-wrench"></i>
      </div>
      <div
        class="icon"
        @click="selectIcon(3)"
        :class="{ active: activeIcon === 3 }"
      >
        <i class="fas fa-user"></i>
      </div>
      <div
        class="icon"
        @click="selectIcon(4)"
        :class="{ active: activeIcon === 4 }"
      >
        <i class="fas fa-shopping-cart"></i>
      </div>
      <div
        class="icon"
        @click="selectIcon(5)"
        :class="{ active: activeIcon === 5 }"
      >
        <i class="fas fa-envelope"></i>
      </div>
      <div
        class="icon"
        @click="selectIcon(6)"
        :class="{ active: activeIcon === 6 }"
      >
        <i class="fas fa-bell"></i>
      </div>
      <div
        class="icon"
        @click="selectIcon(7)"
        :class="{ active: activeIcon === 7 }"
      >
        <i class="fas fa-chart-bar"></i>
      </div>
      <div
        class="icon"
        @click="selectIcon(8)"
        :class="{ active: activeIcon === 8 }"
      >
        <i class="fas fa-cog"></i>
      </div>
      <div
        class="icon"
        @click="selectIcon(9)"
        :class="{ active: activeIcon === 9 }"
      >
        <i class="fas fa-question-circle"></i>
      </div>
    </div>
    <div class="plus-icon">
      <i class="fas fa-plus"></i>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      activeIcon: null,
    };
  },
  methods: {
    selectIcon(iconNumber) {
      this.activeIcon = iconNumber;
    },
  },
};
</script>

<style>
.sidebar {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  align-items: center;
  padding: 28px 0px 0px;
  gap: 28px;
  position: absolute;
  width: 72px;
  left: 0px;
  top: 0%;
  bottom: 0%;
  background: #ffffff;
}

.icons {
  display: flex;
  flex-direction: column;
  gap: 16px;
}

.icon {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 40px;
  height: 40px;
  border-radius: 50%;
}

.icon.active {
  background-color: violet;
}

.plus-icon {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 40px;
  height: 40px;
  border-radius: 50%;
}
</style>
