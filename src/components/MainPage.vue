<template>
  <div class="main-page">
    <div class="team-info">
      <div class="card">
        <div class="team">
          <div class="icon"></div>
          <div class="text">
            <div class="teamText">Team</div>
            <div class="teamInfo">
              <div class="znak">&#xa1;</div>
            </div>
          </div>
        </div>
        <div class="info">
          <div class="members">
            <span class="h">130</span>
            <div class="greyText">members</div>
          </div>
          <div class="palka"></div>
          <div class="online">
            <span class="h">36</span>
            <div class="greyText">online</div>
          </div>
          <div class="palka"></div>
          <div class="men">
            <span class="h">50</span>
            <div class="greyText">men</div>
          </div>
          <div class="women">
            <span class="h">80</span>
            <div class="greyText">women</div>
          </div>
          <div class="palka"></div>
          <div class="averageAge">
            <span class="h">29</span>
            <div class="greyTextt row">average age</div>
          </div>
          <div class="palka"></div>
          <div class="daysWork">
            <span class="h">265</span>
            <div class="greyText">days work on average</div>
          </div>
          <div class="palka"></div>
          <div class="newest">
            <span class="h">36</span>
            <div class="greyText">days work newest employee</div>
          </div>
          <div class="palka"></div>
          <div class="oldest">
            <span class="h">1256</span>
            <div class="greyText">days work oldest employee</div>
          </div>
        </div>
      </div>
    </div>
    <div class="button">
      <div class="plus">
        <div class="plus2">+</div>
      </div>
      <div class="buttonText">Add new Employee</div>
    </div>
    <div class="table">
      <div class="tableTitle">
        <div class="subblock">
          <div class="bissenes">
            <div class="bis">
              <i class="fas fa-search"></i>
              Business Name
              <i
                class="fas fa-chevron-up"
                @click="sortColumn('businessName', 'asc')"
              ></i>
              <i
                class="fas fa-chevron-down"
                @click="sortColumn('businessName', 'desc')"
              ></i>
            </div>
          </div>
          <div class="palka2"></div>
          <div class="teamTable">
            <div class="teamfirst">
              <i class="fas fa-times"></i>
              Team
              <i
                class="fas fa-chevron-up"
                @click="sortColumn('team', 'asc')"
              ></i>
              <i
                class="fas fa-chevron-down"
                @click="sortColumn('team', 'desc')"
              ></i>
            </div>
            <div class="teamSecond">
              <i class="fas fa-chevron-down"></i>
            </div>
          </div>
          <div class="palka2"></div>
          <div class="teamTable">
            <div class="teamfirst">
              <i class="fas fa-times"></i>
              Role
              <i
                class="fas fa-chevron-up"
                @click="sortColumn('role', 'asc')"
              ></i>
              <i
                class="fas fa-chevron-down"
                @click="sortColumn('role', 'desc')"
              ></i>
            </div>
            <div class="teamSecond">
              <i class="fas fa-chevron-down"></i>
            </div>
          </div>
          <div class="palka2"></div>
          <div class="bissenes">
            <div class="bis">
              <i class="fas fa-search"></i>
              Gmail
              <i
                class="fas fa-chevron-up"
                @click="sortColumn('gmail', 'asc')"
              ></i>
              <i
                class="fas fa-chevron-down"
                @click="sortColumn('gmail', 'desc')"
              ></i>
            </div>
          </div>
          <div class="palka2"></div>
          <div class="teamTable">
            <div class="teamfirst">
              <i class="fas fa-times"></i>
              Birthday
              <i
                class="fas fa-chevron-up"
                @click="sortColumn('birthday', 'asc')"
              ></i>
              <i
                class="fas fa-chevron-down"
                @click="sortColumn('birthday', 'desc')"
              ></i>
            </div>
            <div class="teamSecond">
              <i class="fas fa-chevron-down"></i>
            </div>
          </div>
          <div class="palka2"></div>
          <div class="bissenes">
            <div class="bis">
              Telegram
              <i
                class="fas fa-chevron-up"
                @click="sortColumn('telegram', 'asc')"
              ></i>
              <i
                class="fas fa-chevron-down"
                @click="sortColumn('telegram', 'desc')"
              ></i>
            </div>
          </div>
          <div class="palka2"></div>
          <div class="bissenes">
            <div class="bis">
              Last Login
              <i
                class="fas fa-chevron-up"
                @click="sortColumn('lastLogin', 'asc')"
              ></i>
              <i
                class="fas fa-chevron-down"
                @click="sortColumn('lastLogin', 'desc')"
              ></i>
            </div>
          </div>
          <div class="palka2"></div>
          <div class="bissenes">
            <div class="bis">User permissions</div>
          </div>
        </div>
      </div>
      <div class="childlines">
        <div class="people1" v-for="person in sortedPeople" :key="person.id">
          <div class="photos">
            <img :src="getAssetPath(person.photo)" alt="" />
            <p>{{ person.name ? person.name : '' }}</p>
          </div>
          <div class="teams">{{ person.team }}</div>
          <div class="lead">{{ person.role }}</div>
          <div class="mail">{{ person.gmail }}</div>
          <div class="birthday">{{ person.birthday }}</div>
          <div class="teleg">{{ person.telegram }}</div>
          <div class="last">{{ person.lastLogin }}</div>
          <div class="crud">
            <i class="fas fa-pencil-alt"></i><i class="fas fa-trash-alt"></i>
          </div>
        </div>
      </div>
    </div>
    <div class="pagination">
      <div
        class="number strelka"
        v-if="activeNumber > 1"
        @click="changeActiveNumber(activeNumber - 1)"
      >
        &lt;
      </div>
      <div
        class="number"
        :class="{ active: activeNumber === number }"
        v-for="number in displayedNumbers"
        :key="number"
        @click="changeActiveNumber(number)"
      >
        {{ number }}
      </div>
      <div
        class="number strelka"
        v-if="activeNumber < numbers.length"
        @click="changeActiveNumber(activeNumber + 1)"
      >
        &gt;
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      numbers: Array.from({ length: 12 }, (_, index) => index + 1),
      activeNumber: 2,
      columnSortKey: '',
      columnSortOrder: 'asc',
      people: [
        {
          id: 1,
          photo: 'Logo.png',
          name: 'Sarah Connor',
          team: 'Crosty',
          role: 'Team Lead',
          gmail: 'sarahconnor@gmail.com',
          birthday: '24.04.1994',
          telegram: '@sarahconnor',
          lastLogin: '03.11.2021',
        },
        {
          id: 2,
          photo: 'Logo2.png',
          name: 'Ernest Eberly',
          team: 'Flamethrower',
          role: 'Semantic Specialist',
          gmail: 'ernesteberly@gmail.com',
          birthday: '17.06.1993',
          telegram: '@ErnestEberly',
          lastLogin: '03.11.2021',
        },
        {
          id: 3,
          photo: 'Logo1.png',
          name: 'Lance Thomas',
          team: 'Wizards',
          role: 'Seo Specialist',
          gmail: 'lancethomas@gmail.com',
          birthday: '12.04.1989',
          telegram: '@LanceThomas',
          lastLogin: '01.11.2021',
        },
        {
          id: 4,
          photo: 'Logo1.png',
          name: 'Lance Thomas',
          team: 'Wizards',
          role: 'Seo Specialist',
          gmail: 'lancethomas@gmail.com',
          birthday: '12.04.1989',
          telegram: '@LanceThomas',
          lastLogin: '01.11.2021',
        },
        {
          id: 5,
          photo: 'Logo1.png',
          name: 'Lance Thomas',
          team: 'Wizards',
          role: 'Seo Specialist',
          gmail: 'lancethomas@gmail.com',
          birthday: '12.04.1989',
          telegram: '@LanceThomas',
          lastLogin: '01.11.2021',
        },
        {
          id: 6,
          photo: 'Logo1.png',
          name: 'Lance Thomas',
          team: 'Wizards',
          role: 'Seo Specialist',
          gmail: 'lancethomas@gmail.com',
          birthday: '12.04.1989',
          telegram: '@LanceThomas',
          lastLogin: '01.11.2021',
        },
        {
          id: 7,
          photo: 'Logo1.png',
          name: 'Lance Thomas',
          team: 'Wizards',
          role: 'Seo Specialist',
          gmail: 'lancethomas@gmail.com',
          birthday: '12.04.1989',
          telegram: '@LanceThomas',
          lastLogin: '01.11.2021',
        },
        {
          id: 8,
          photo: 'Logo1.png',
          name: 'Lance Thomas',
          team: 'Wizards',
          role: 'Seo Specialist',
          gmail: 'lancethomas@gmail.com',
          birthday: '12.04.1989',
          telegram: '@LanceThomas',
          lastLogin: '01.11.2021',
        },
        {
          id: 9,
          photo: 'Logo1.png',
          name: 'Lance Thomas',
          team: 'Wizards',
          role: 'Seo Specialist',
          gmail: 'lancethomas@gmail.com',
          birthday: '12.04.1989',
          telegram: '@LanceThomas',
          lastLogin: '01.11.2021',
        },
      ],
    };
  },
  computed: {
    displayedNumbers() {
      return this.numbers.slice(0, 3);
    },
    sortedPeople() {
      let sortedPeople = [...this.people];

      if (this.columnSortKey) {
        sortedPeople.sort((a, b) => {
          let aValue = a[this.columnSortKey] || '';
          let bValue = b[this.columnSortKey] || '';

          if (this.columnSortOrder === 'asc') {
            return aValue.localeCompare(bValue);
          } else {
            return bValue.localeCompare(aValue);
          }
        });
      }

      return sortedPeople;
    },
  },
  methods: {
    changeActiveNumber(number) {
      this.activeNumber = number;
    },
    sortColumn(key, order) {
      this.columnSortKey = key;
      this.columnSortOrder = order;
    },
    getAssetPath(path) {
      return require(`../assets/${path}`);
    },
  },
};
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Commissioner:wght@500&family=Roboto:wght@100;400&display=swap');
.znak {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  color: #8591ae;
}
.crud {
  display: flex;
  flex-direction: row;
  align-items: center;
  gap: 10px;
  justify-content: space-between;
  width: 50px;
  height: 64px;
}
.teleg {
  display: flex;
  flex-direction: row;
  align-items: center;
  gap: 10px;
  width: 221.14px;
  height: 64px;
}
.last {
  display: flex;
  flex-direction: row;
  align-items: center;
  gap: 10px;
  width: 221.14px;
  height: 64px;
}
.mail {
  display: flex;
  flex-direction: row;
  align-items: center;
  gap: 10px;
  width: 221.14px;
  height: 64px;
}
.birthday {
  display: flex;
  flex-direction: row;
  align-items: center;
  gap: 10px;
  width: 250px;
  height: 64px;
}
.lead {
  display: flex;
  flex-direction: row;
  align-items: center;
  gap: 10px;
  width: 285px;
  height: 64px;
}
.teams {
  display: flex;
  flex-direction: row;
  align-items: center;
  gap: 10px;
  width: 300px;
  height: 64px;
}
.photos {
  display: flex;
  flex-direction: row;
  align-items: center;
  gap: 12px;
  width: 221.14px;
  height: 64px;
}
.people1 {
  display: flex;
  flex-direction: row;
  align-items: flex-start;
  padding: 0px;
  width: 1760px;
  height: 60px;
  border-radius: 12px;
}
.childlines {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  padding: 0px;
  width: 1760px;
  height: 584px;
}

.teamfirst {
  display: flex;
  align-items: center;
  gap: 8px;
}
.teamTable {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
  padding: 22px 16px;
  gap: 12px;

  width: 221.14px;
  height: 64px;
}

.bis {
  display: flex;
  align-items: center;
  gap: 8px;
}
.bissenes {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin: 10px;
}
.palka2 {
  width: 1px;
  height: 64px;
  background-color: #e5e8ef;
}
.tableTitle {
  display: flex;
  flex-direction: row;
  align-items: center;
  padding: 0px;
  width: 1760px;
  height: 64px;
  background: #f5f7fb;
  border-radius: 12px;
}

.subblock {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
  flex-grow: 1;
  height: 100%;
}
.newest {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  padding: 0px;
  width: 152px;
  height: 47px;
}
.daysWork {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  padding: 0px;
  width: 116px;
  height: 47px;
}
.row {
  display: flex;
  flex-direction: row;
}
.oldest {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  padding: 0px;
  width: 146px;
  height: 47px;
}
.table {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  padding: 16px;
  width: 1760px;
  height: 680px;
  background: #ffffff;
  border-radius: 12px;
}
.greyTextt {
  display: inline;
  white-space: nowrap;
  font-family: 'Commissioner';
  font-style: normal;
  font-weight: 400;
  font-size: 12px;
  line-height: 150%;
  color: #8591ae;
  vertical-align: middle;
}

.averageAge {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  padding: 0px;
  width: 64px;
  height: 47px;
}
.women {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  padding: 0px;
  width: 41px;
  height: 47px;
}
.men {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  padding: 0px;
  width: 28px;
  height: 47px;
}
.h {
  box-sizing: border-box;
  width: 27px;
  height: 29px;
  font-family: 'Commissioner';
  font-style: normal;
  font-weight: 500;
  font-size: 22px;
  line-height: 130%;
  color: #2a355a;
}
.online {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  padding: 0px;
  width: 43px;
  height: 47px;
}
.palka {
  width: 47px;
  height: 0px;
  border: 1px solid #e5e8ef;
  transform: rotate(90deg);
}
.greyText {
  display: inline;
  white-space: nowrap;
  width: 51px;
  height: 18px;
  font-family: 'Commissioner';
  font-style: normal;
  font-weight: 400;
  font-size: 12px;
  line-height: 150%;
  color: #8591ae;
}
.members {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
}
.teamText {
  width: 35px;
  height: 20px;
  font-family: 'Commissioner';
  font-style: normal;
  font-weight: 500;
  font-size: 14px;
  line-height: 20px;
  color: #2a355a;
}
.teamInfo {
  position: relative;
  width: 14px;
  height: 14px;
  background: #f5f7fb;
  border-radius: 1000px;
}
.icon {
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
  padding: 0px;
  gap: 10px;
  width: 32px;
  height: 32px;
  background: #f3f9ff;
  border-radius: 8px;
}
.text {
  display: flex;
  flex-direction: row;
  align-items: flex-start;
  padding: 0px;
  gap: 4px;
  width: 53px;
  height: 20px;
}
.team {
  display: flex;
  flex-direction: row;
  align-items: center;
  padding: 0px;
  gap: 16px;
  width: 101px;
  height: 47px;
}
.info {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: center;
  padding: 0px;
  gap: 30px;
  width: 1174px;
  height: 47px;
}
.main-page {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  padding: 28px;
  gap: 28px;
  position: absolute;
  height: 900px;
  left: 72px;
  right: 0px;
  top: 76px;
}
.team-info {
  display: flex;
  flex-direction: row;
  align-items: flex-start;
  gap: 16px;
  width: 100%;
  max-width: 1460px;
  height: 79px;
  background: #ffffff;
  border-radius: 12px;
  justify-content: center;
  margin-bottom: 50px;
}
.card {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: center;
  padding: 16px 28px;
  gap: 72px;
  width: 1403px;
  height: 79px;
  background: #ffffff;
  border-radius: 12px;
}
.button {
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
  padding: 20px;
  gap: 12px;
  width: 184px;
  height: 48px;
  background: #8f20ef;
  border-radius: 12px;
}
.buttonText {
  width: 120px;
  height: 20px;
  font-family: 'Commissioner';
  font-style: normal;
  font-weight: 400;
  font-size: 14px;
  line-height: 20px;
  color: #ffffff;
  white-space: nowrap;
}
.plus {
  width: 20px;
  height: 20px;
  background: rgba(255, 255, 255, 0.2);
  border-radius: 6px;
}
.plus2 {
  display: flex;
  justify-content: center;
  text-align: center;
  color: white;
}
.pagination {
  display: flex;
  align-items: center;
  justify-content: flex-start;
  padding: 16px;
  gap: 8px;
  width: 1792px;
  height: 68px;
  background: #ffffff;
  border-radius: 12px;
}

.number {
  width: 32px;
  height: 32px;
  display: flex;
  justify-content: center;
  align-items: center;
  border-radius: 6px;
  cursor: pointer;
  color: #8591ae;
}

.number.active {
  background: #f5f7fb;
  color: black;
}

.ellipsis {
  display: flex;
  align-items: center;
  color: #2a355a;
}
.strelka {
  color: #8591ae;
  background: #f5f7fb;
}
</style>
