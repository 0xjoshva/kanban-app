<template>
  <nav>
    <div class="logo" v-if="isSidebarOpen === false">
      <img src="../assets/logo-light.svg" alt="" v-if="isDark === true" />
      <img src="../assets/logo-dark.svg" alt="" v-if="isDark === false" />
    </div>
    <div class="placeholder" v-if="isSidebarOpen === true"></div>
    <div class="right-nav">
      <p class="page-name">Platform Launch</p>
      <div class="buttons">
        <button class="newtask-btn">
          <img src="../assets/icon-add-task-mobile.svg" alt="" /> Add New Task
        </button>
        <button class="edit-board-btn">
          <img src="../assets/icon-vertical-ellipsis.svg" alt="" />
        </button>
      </div>
    </div>
  </nav>





  <div :class="['sidebar', { 'slide-in': isSidebarOpen }]">
    <div class="inner-sidebar">
      <div class="start">
        <div class="s-logo">
          <img src="../assets/logo-light.svg" alt="" v-if="isDark === true" />
          <img src="../assets/logo-dark.svg" alt="" v-if="isDark === false" />
        </div>
        <p class="all-boards" v-for="board in boards" :key="board.name">
          ALL BOARDS ({{ board.length }})
        </p>
        <div class="nav-items" v-for="board in boards" :key="board.name">
          <div class="board-btn" v-for="item in board" :key="item.name">
            <svg width="16" height="16" xmlns="http://www.w3.org/2000/svg">
              <path
                d="M0 2.889A2.889 2.889 0 0 1 2.889 0H13.11A2.889 2.889 0 0 1 16 2.889V13.11A2.888 2.888 0 0 1 13.111 16H2.89A2.889 2.889 0 0 1 0 13.111V2.89Zm1.333 5.555v4.667c0 .859.697 1.556 1.556 1.556h6.889V8.444H1.333Zm8.445-1.333V1.333h-6.89A1.556 1.556 0 0 0 1.334 2.89V7.11h8.445Zm4.889-1.333H11.11v4.444h3.556V5.778Zm0 5.778H11.11v3.11h2a1.556 1.556 0 0 0 1.556-1.555v-1.555Zm0-7.112V2.89a1.555 1.555 0 0 0-1.556-1.556h-2v3.111h3.556Z"
              />
            </svg>
            {{ item.name }}
          </div>
        </div>
        <button class="board-btn create-new-board">
          <img src="../assets/icon-board.svg" alt="" />
          <!-- <svg width="12" height="12" xmlns="http://www.w3.org/2000/svg"><path fill="" d="M7.368 12V7.344H12V4.632H7.368V0H4.656v4.632H0v2.712h4.656V12z"/></svg> -->
          + Create New Board
        </button>
      </div>
      <div class="end">
        <div class="toggle-theme">
          <img src="../assets/icon-dark-theme.svg" alt="" />

          <div class="toggler">
            <input
              type="checkbox"
              id="toggle"
              class="offscreen"
              @click="toggleTheme()"
            />
            <label for="toggle" class="switch"></label>
          </div>
          <img src="../assets/icon-light-theme.svg" alt="" />
        </div>
        <button class="hide-sidebar" @click="toggleSidebar()">
          <img src="../assets/icon-hide-sidebar.svg" alt="" /> Hide Sidebar
        </button>
      </div>
    </div>
    <button
      v-if="isSidebarOpen === false"
      @click="toggleSidebar()"
      class="show-sidebar"
    >
      <img src="../assets/icon-show-sidebar.svg" alt="" />
    </button>
  </div>
</template>
<script>
import dataJSON from "/data/data.json";
export default {
  data() {
    return {
      boards: dataJSON,
      isSidebarOpen: false,
      isDark: true,
    };
  },
  methods: {
    toggleSidebar() {
      this.isSidebarOpen = !this.isSidebarOpen;
    },
    toggleTheme() {
      this.isDark = !this.isDark;
    },
  },
  computed: {
    itemCount() {
      return this.boards.board.length;
    },
  },
};
</script>
<style lang="scss" scoped>
$VeryDarkBG: #20212c;
$DarkGrey: #2b2c37;
$LinesDark: #3e3f4e;
$MediumGrey: #828fa3;
$LinesLight: #e4ebfa;
$LightGreyLightBG: #f4f7fd;

$Black: #000112;
$White: #ffffff;
$Purple: #635fc7;
$PurpleHover: #a8a4ff;
$Red: #ea5555;
$RedHover: #ff9898;

$HeadingXL: 24px;
$HeadingL: 18px;
$HeadingM: 15px;
$HeadingS: 12px;

$PrimaryColor: $DarkGrey;
$PrimaryLineColor: $LinesDark;

.theme-dark {
  --bg-primary: $DarkGrey;
  --lines: $LinesDark;
}

.theme-light {
  --bg-primary: $White;
  --lines: $LinesLight;
}
nav {
  width: 100%;
  height: 97px;
  background: $PrimaryColor;
  border-bottom: 1px solid $PrimaryLineColor;
  display: flex;
  z-index: 1;
  position: fixed;

  .logo {
    width: 210px;
    border-right: $PrimaryLineColor 1px solid;
    height: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
  }
  .right-nav {
    width: 100%;
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding-inline: 2rem;

    .page-name {
      color: $White;
      font-size: $HeadingXL;
      font-weight: 700;
    }
    .buttons {
      display: flex;
      column-gap: 1rem;

      .newtask-btn {
        display: flex;
        justify-content: center;
        align-items: center;
        column-gap: 0.5rem;
        width: 164px;
        height: 48px;
        border-radius: 24px;
        border: none;
        outline: none;
        background: $Purple;
        color: $White;
        font-size: $HeadingM;
        font-weight: 700;
        transition: ease all 0.4s;
        cursor: pointer;

        &:hover:not([disabled]) {
          background: $PurpleHover;
        }
      }
      .edit-board-btn {
        background: transparent;
        border: none;
        outline: none;
        cursor: pointer;
      }
    }
  }
}
.sidebar {
  position: absolute;
  width: fit-content;
  height: 100%;
  background: transparent;
  z-index: 10;
  transform: translateX(-91%);
  transition: transform 0.4s ease;
  display: flex;
  justify-content: flex-end;
  align-items: flex-end;

  .show-sidebar {
    background: $Purple;
    border: none;
    outline: none;
    width: fit-content;
    height: fit-content;
    padding: 1rem;
    padding-left: 13rem;
    border-top-right-radius: 26px;
    border-bottom-right-radius: 26px;
    margin-bottom: 2.5rem;
    animation: slide-in .5s ease;
    cursor: pointer;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .inner-sidebar {
    width: 300px;
    height: 100%;
    background: $PrimaryColor;
    border-right: 1px solid $PrimaryLineColor;
    display: flex;
    justify-content: space-between;
    flex-direction: column;
  }
  .s-logo {
    height: 97px;
    width: 100%;
    display: flex;
    justify-content: start;
    padding-left: 2rem;
    align-items: center;
    display: flex;
  }
  .all-boards {
    font-size: 12px;
    color: $MediumGrey;
    letter-spacing: 2.4px;
    font-weight: bold;
    padding-left: 2rem;
  }
  .nav-items {
    padding-top: 1rem;

    .board-btn {
      width: 276px;
      height: 48px;
      border-top-right-radius: 26px;
      border-bottom-right-radius: 26px;
      font-size: $HeadingM;
      background: transparent;
      display: flex;
      align-items: center;
      justify-content: start;
      text-decoration: none;
      color: $MediumGrey;
      font-weight: bold;
      column-gap: 1rem;
      padding-left: 2rem;

      svg {
        fill: #828fa3;
      }
    }
    .router-link-active {
      background: $Purple !important;

      color: $White !important;
      fill: white !important;
      text-decoration: none;
      font-weight: bold;

      svg {
        fill: $White;
      }
    }
  }

  .create-new-board {
    color: $Purple;
    width: 276px;
    height: 48px;
    border-top-right-radius: 26px;
    border-bottom-right-radius: 26px;
    font-size: $HeadingM;
    background: transparent;
    display: flex;
    align-items: center;
    justify-content: start;
    text-decoration: none;
    font-weight: bold;
    column-gap: 1rem;
    padding-left: 2rem;
    border: none;
    outline: none;
    cursor: pointer;
  }
  .create-new-board svg {
    fill: $Purple !important;
  }

  .end {
    height: fit-content;
    width: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
    padding-bottom: 2rem;
    row-gap: 0.5rem;
    .toggle-theme {
      background: $VeryDarkBG;
      width: 251px;
      height: 48px;
      border-radius: 6px;
      display: flex;
      justify-content: center;
      align-items: center;
      column-gap: 1rem;

      .toggler {
        transform: translateY(3px);
      }
    }
    .hide-sidebar {
      display: flex;
      align-items: center;
      justify-content: start;
      width: 251px;
      height: 48px;
      color: $MediumGrey;
      font-size: $HeadingM;
      font-weight: bold;
      column-gap: 0.5rem;
      background: transparent;
      border: none;
      outline: none;
      cursor: pointer;
    }
  }
}
.slide-in {
  transform: translateX(0);
}
.placeholder {
  width: 340px;
  height: 100%;
  animation: ease grow-in 0.4s;
}
@keyframes grow-in {
  0% {
    width: 0px;
  }
  100% {
    width: 340px;
  }
}

@keyframes slide-in {
  0% {
    transform: translateX(-400%);
  }
  100% {
    transform: translateX(0);
  }
}

.switch {
  position: relative;
  display: inline-block;
  width: 42px;
  height: 22px;
  background-color: $Purple;
  border-radius: 20px;
  transition: all 0.3s;
  cursor: pointer;
}

.switch::after {
  content: "";
  position: absolute;
  width: 14px;
  height: 14px;
  border-radius: 14px;
  background-color: white;
  top: 4px;
  left: 4px;
  transition: all 0.3s;
}

input[type="checkbox"]:checked + .switch::after {
  transform: translateX(20px);
}

input[type="checkbox"]:checked + .switch {
  background-color: $Purple;
}

.offscreen {
  position: absolute;
  left: -9999px;
}
</style>
