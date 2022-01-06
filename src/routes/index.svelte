<script lang="ts">
  import {
    mdiCircleSmall,
    mdiBasket,
    mdiAnvil,
    mdiArrowDecisionOutline,
    mdiAudioVideo,
    mdiPencil,
    mdiBaguette,
    mdiCar,
    mdiIceCream,
    mdiHexagonSlice4,
    mdiGamepadCircle,
    mdiMotion,
    mdiHandHeart,
    mdiCalendar,
    mdiEmail,
    mdiNote,
    mdiCog,
    mdiPhone,
    mdiChat,
    mdiClock,
    mdiAlarm,
    mdiCalculator,
    mdiCamera,
    mdiFlashlight,
    mdiTelevision,
    mdiCctv,
    mdiTrophyVariant,
    mdiShieldMoon,
    mdiSword,
    mdiCircleOpacity,
    mdiMapMarkerRadius,
    mdiFoodDrumstick,
    mdiBank
  } from '@mdi/js';

  type App = {
    name: string;
    icon: string;
    bgColor?: string;
    color?: string;
    size?: number;
    onClick?: () => void;
  };

  // Additional apps if you need different ones / more:
  const _unusedApps: App[] = [
    {
      name: 'Scralb Immel',
      icon: mdiArrowDecisionOutline,
      bgColor: '#D83999',
      color: '#D9D700'
    },
    {
      name: 'Echo InCotro',
      icon: mdiAudioVideo,
      bgColor: '#000',
      color: '#1E1597'
    },
    {
      name: 'Chefrom',
      icon: mdiAnvil,
      bgColor: '#426BC2',
      color: '#C38BE5'
    },
    {
      name: 'Flashlight',
      icon: mdiFlashlight,
      bgColor: '#3B3B46',
      color: '#E2E2EE'
    }
  ];

  let apps: App[] = [
    {
      name: 'Vingus',
      icon: mdiBasket,
      bgColor: '#ff3',
      color: '#000'
    },
    {
      name: 'Spencillo',
      icon: mdiPencil,
      bgColor: '#FFF895',
      color: '#D98200'
    },
    {
      name: 'Baguette',
      icon: mdiBaguette,
      bgColor: '#D93400',
      color: '#FFAB44'
    },
    {
      name: 'Geliito',
      icon: mdiIceCream,
      bgColor: '#000',
      color: '#FFF'
    },
    {
      name: 'Jorius Kamus',
      icon: mdiHexagonSlice4,
      bgColor: '#0B4B8E',
      color: '#FFF'
    },
    {
      name: 'Lilly Omno',
      icon: mdiGamepadCircle,
      bgColor: '#009161',
      color: '#86E4C5'
    },
    {
      name: 'ThreadChain',
      icon: mdiMotion,
      bgColor: '#000',
      color: '#8CB7E3'
    },
    {
      name: 'Love Love',
      icon: mdiHandHeart,
      bgColor: '#FFF',
      color: '#D20014'
    },
    {
      name: 'Calendar',
      icon: mdiCalendar,
      bgColor: '#3B3B46',
      color: '#E2E2EE'
    },
    {
      name: 'Email',
      icon: mdiEmail,
      bgColor: '#3B3B46',
      color: '#E2E2EE'
    },
    {
      name: 'Notes',
      icon: mdiNote,
      bgColor: '#3B3B46',
      color: '#E2E2EE'
    },
    {
      name: 'Settings',
      icon: mdiCog,
      bgColor: '#3B3B46',
      color: '#E2E2EE'
    },
    {
      name: 'Clock',
      icon: mdiClock,
      bgColor: '#3B3B46',
      color: '#E2E2EE'
    },
    {
      name: 'Alarms',
      icon: mdiAlarm,
      bgColor: '#3B3B46',
      color: '#E2E2EE'
    },
    {
      name: 'Calculator',
      icon: mdiCalculator,
      bgColor: '#3B3B46',
      color: '#E2E2EE'
    },
    {
      name: 'Wenflick',
      icon: mdiTelevision,
      bgColor: '#C62020',
      color: '#FFF'
    },
    {
      name: 'Home Watch',
      icon: mdiCctv,
      bgColor: '#A32373',
      color: '#FFF'
    },
    {
      name: 'Victorious',
      icon: mdiTrophyVariant,
      bgColor: '#2C0971',
      color: '#FFE63D'
    },
    {
      name: 'Night Stone',
      icon: mdiShieldMoon,
      bgColor: '#160D73',
      color: '#CCC'
    },
    {
      name: 'Trel Warrior',
      icon: mdiSword,
      bgColor: '#3C0770',
      color: '#CCC'
    },
    {
      name: 'Morphilix',
      icon: mdiCircleOpacity,
      bgColor: '#000',
      color: '#F075BD'
    },
    {
      name: 'Waystop',
      icon: mdiMapMarkerRadius,
      bgColor: '#FFF',
      color: '#078600'
    },
    {
      name: 'Dedgebone',
      icon: mdiFoodDrumstick,
      bgColor: '#FFEAC4',
      color: '#5E2700'
    },
    {
      name: 'First Second Bank',
      icon: mdiBank,
      bgColor: '#B9F1B9',
      color: '#004C00'
    }
  ].sort((a, b) => a.name.localeCompare(b.name));
  const removedApps: App[] = [];

  const tray: App[] = [
    {
      name: 'Phone',
      icon: mdiPhone,
      bgColor: '#3B3B46',
      color: '#E2E2EE',
      onClick: () => {
        if (apps.length) {
          removedApps.push(apps.splice(apps.length - 1, 1)[0]);
          apps = apps;
        }
      }
    },
    {
      name: 'Messages',
      icon: mdiChat,
      bgColor: '#3B3B46',
      color: '#E2E2EE',
      onClick: () => {
        if (removedApps.length) {
          apps.push(removedApps.splice(removedApps.length - 1, 1)[0]);
          apps = apps;
        }
      }
    },
    {
      name: 'Kangroo',
      icon: mdiCar,
      bgColor: '#FF6E44',
      color: '#FFF',
      onClick: () => (appsVisible = !appsVisible)
    },
    {
      name: 'Camera',
      icon: mdiCamera,
      bgColor: '#3B3B46',
      color: '#E2E2EE',
      onClick: toggleFullscreen
    }
  ];

  let appsVisible = true;

  async function toggleFullscreen() {
    if (document.fullscreenElement) {
      document.exitFullscreen();
    } else {
      try {
        await document.documentElement.requestFullscreen({
          navigationUI: 'hide'
        });
      } catch (e: any) {
        // ignore error
      }
    }
  }
</script>

<div class="container">
  <div class="cloud cloud-left" />
  <div class="cloud cloud-right" />

  <div class="screen" class:apps-visible={appsVisible}>
    {#each apps as app}
      <div class="app" on:click={app.onClick || (() => {})}>
        <div
          class="logo"
          style="{app.bgColor ? `background-color: ${app.bgColor};` : ''} {app.color
            ? `color: ${app.color};`
            : ''}"
        >
          <svg
            class="icon"
            viewBox="0 0 24 24"
            style={app.size ? `height: ${app.size}px; width: ${app.size}px;` : ''}
          >
            <path fill="currentColor" d={app.icon} />
          </svg>
        </div>
        <div class="name">{app.name}</div>
      </div>
    {/each}
  </div>

  <div class="pager" class:apps-visible={appsVisible}>
    <svg viewBox="0 0 24 24">
      <path fill="currentColor" d={mdiCircleSmall} />
    </svg>
    <svg viewBox="0 0 24 24">
      <path fill="currentColor" d={mdiCircleSmall} />
    </svg>
  </div>

  <div class="tray">
    {#each tray as app}
      <div class="app" on:click={app.onClick || (() => {})}>
        <div
          class="logo"
          style="{app.bgColor ? `background-color: ${app.bgColor};` : ''} {app.color
            ? `color: ${app.color};`
            : ''}"
        >
          <svg
            class="icon"
            viewBox="0 0 24 24"
            style={app.size ? `height: ${app.size}px; width: ${app.size}px;` : ''}
          >
            <path fill="currentColor" d={app.icon} />
          </svg>
        </div>
        <div class="name">{app.name}</div>
      </div>
    {/each}
  </div>
</div>

<style>
  :global(html, body) {
    height: 100%;
    width: 100%;
    padding: 0;
    margin: 0;
  }

  :global(body) {
    background: rgba(76, 63, 145);
    background: linear-gradient(
      rgba(76, 63, 145, 1),
      rgba(76, 63, 145, 1) 60%,
      rgba(145, 69, 182, 1) 70%,
      rgba(185, 88, 165, 1) 80%,
      rgba(255, 86, 119, 1) 90%,
      rgba(240, 210, 144, 1) 100%
    );
    background-blend-mode: screen;
    background-size: cover;
    color: white;
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  }

  :global(#svelte) {
    height: 100%;
  }

  .container {
    display: flex;
    height: 100%;
    width: 100%;
    overflow: hidden;
    flex-direction: column;
    justify-content: space-between;
    padding: 0 0 16px;
    box-sizing: border-box;
  }

  .screen,
  .tray {
    display: flex;
    flex-wrap: wrap;
    justify-content: flex-start;
    align-items: flex-start;
    position: relative;
  }

  .tray::before {
    content: ' ';
    display: block;
    position: absolute;
    top: 4px;
    right: 4px;
    bottom: 4px;
    left: 4px;
    background-color: #000;
    z-index: -1;
    border-radius: 22px;
    opacity: 0.2;
  }

  .pager {
    flex-grow: 1;
    display: flex;
    justify-content: center;
    align-items: flex-end;
    margin-bottom: 16px;
  }
  .pager svg {
    height: 14px;
    width: 14px;
    transform: scale(3);
    opacity: 0.4;
  }
  .pager.apps-visible svg:first-child {
    opacity: 0.9;
  }
  .pager:not(.apps-visible) svg:last-child {
    opacity: 0.9;
  }

  .app {
    display: flex;
    flex-direction: column;
    align-items: center;
    flex-wrap: wrap;
    width: calc(100% / 4);
    margin-top: 22px;
  }

  .screen .app {
    visibility: hidden;
  }
  .screen.apps-visible .app {
    visibility: visible;
  }

  .tray .app {
    margin-bottom: 22px;
  }

  .logo {
    background-color: black;
    height: 56px;
    width: 56px;
    display: flex;
    justify-content: center;
    align-items: center;
    border-radius: 16px;
    box-shadow: inset -5px -5px 25px -15px rgba(0, 0, 0, 0.2),
      inset 5px 5px 25px -15px rgba(255, 255, 255, 0.2);
  }

  .icon {
    width: 40px;
    height: 40px;
  }

  .name {
    text-align: center;
    font-weight: 500;
    margin-top: 5px;
    font-size: 12px;
    text-shadow: 1px 1px 2px #000;
    white-space: nowrap;
    text-overflow: ellipsis;
    overflow-x: hidden;
    width: 100%;
  }

  .tray .name {
    display: none;
  }

  .cloud {
    position: absolute;
    background: linear-gradient(rgb(10, 25, 49), rgb(10, 25, 49) 85%, rgba(243, 149, 13, 1));
    box-shadow: 0 4px 2px 2px rgba(244, 225, 133, 0.8);
    width: 160px;
    height: 45px;
    border-radius: 45px;
    transform: scale(2);
    filter: blur(1px);
  }
  .cloud::after,
  .cloud::before {
    content: ' ';
    display: block;
    position: absolute;
    background: inherit;
    border-radius: 100%;
  }
  .cloud::after {
    width: 60px;
    height: 60px;
    top: -25px;
    left: 15px;
  }
  .cloud::before {
    width: 90px;
    height: 90px;
    top: -45px;
    left: 55px;
  }
  .cloud.cloud-left {
    left: 20px;
    top: 125px;
  }
  .cloud.cloud-right {
    right: 40px;
    top: 155px;
  }
</style>
