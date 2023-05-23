<template>
  <div class="navbar">
    <div class="content">
      <div class="burger">
        <div class="tems">
          <i class="fas fa-bars"></i>
          <div class="slovo">Team</div>
        </div>
      </div>
      <div class="topBar">
        <div class="search">
          <i class="fas fa-search"></i>
          <input type="text" placeholder="Search" disabled />
        </div>
        <div class="bell">
          <i class="fas fa-bell"></i>
        </div>
        <div class="line"></div>
        <div class="profile">
          <div class="photo">
            <img src="../assets/Logo2.png" alt="Profile Photo" />
          </div>
          <div class="name">John Doe</div>
          <div class="arrow">
            <i class="fas fa-chevron-down"></i>
          </div>
          <div class="dropdown">
            <div class="dropdown-item">Item 1</div>
            <div class="dropdown-item">Item 2</div>
            <div class="dropdown-item">Item 3</div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style>
.slovo {
  font-family: 'Commissioner';
  font-style: normal;
  font-weight: 500;
  font-size: 22px;
  line-height: 150%;
  color: #2a355a;
}
.navbar {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: flex-start;
  width: 1850px;
  padding: 0px 0px 0px 72px;
  position: absolute;
  height: 76px;
  left: 0%;
  right: 0%;
  top: 0px;
  background: #ffffff;
  border-top-left-radius: 12px;
  border-top-right-radius: 12px;
}
.content {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
  padding: 0px 28px 0px 0px;
  gap: 10px;
  width: 1848px;
  height: 76px;
}
.burger {
  display: flex;
  flex-direction: row;
  align-items: center;
  padding: 0px;
  gap: 28px;
  width: 127px;
  height: 76px;
}
.topBar {
  display: flex;
  flex-direction: row;
  justify-content: flex-end;
  align-items: center;
  gap: 28px;
  width: 293px;
  height: 32px;
  padding: 20px;
}
.tems {
  display: flex;
  gap: 60px;
  align-items: center;
}

.search {
  display: flex;
  align-items: center;
  gap: 8px;
  height: 32px;
  background: #f5f7fb;
  border-radius: 8px;
  padding: 0px 8px;
}

.search input {
  border: none;
  outline: none;
  background: transparent;
  font-family: 'Commissioner';
  font-style: normal;
  font-weight: 500;
  font-size: 14px;
  line-height: 20px;
  color: #2a355a;
  width: 100%;
}

.bell {
  display: flex;
  align-items: center;
  height: 32px;
  background: #f5f7fb;
  border-radius: 8px;
  padding: 0px 8px;
}

.bell i {
  color: #2a355a;
}

.line {
  height: 35px;
  border: 1px solid #b7b8bb;
}

.profile {
  display: flex;
  align-items: center;
  position: relative; /* Добавлено */
}

.photo img {
  width: 32px;
  height: 32px;
  border-radius: 50%;
}

.name {
  font-family: 'Commissioner';
  font-style: normal;
  font-weight: 500;
  font-size: 14px;
  line-height: 20px;
  color: #2a355a;
  margin-left: 8px;
  white-space: nowrap;
}

.arrow {
  color: #2a355a;
  margin: 15px;
}

/* Дополнительные стили для дропдауна */
.dropdown {
  position: absolute;
  top: 100%; /* Отображается под профилем */
  right: 0; /* Отображается справа от профиля */
  width: 150px;
  background-color: #ffffff;
  border-radius: 8px;
  box-shadow: 0px 4px 10px rgba(0, 0, 0, 0.1);
  display: none; /* По умолчанию скрыт */
  z-index: 1;
}

.dropdown-item {
  padding: 8px 16px;
  font-family: 'Commissioner';
  font-style: normal;
  font-weight: 500;
  font-size: 14px;
  line-height: 20px;
  color: #2a355a;
  cursor: pointer;
}

.profile:hover .dropdown {
  display: block; /* Отображается при наведении на профиль */
}
</style>
