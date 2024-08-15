<template>
  <div>
    <div class="profile-cards-container">
      <div
        v-for="(profile, index) in profiles"
        :key="index"
        class="profile-card"
      >
        <div class="profile-card-header">
          <img :src="profile.avatar" :alt="profile.name" class="avatar" />
          <h3 class="profile-name">{{ profile.name }}</h3>
          <span class="profile-role">{{ profile.role }}</span>
        </div>
        <div class="profile-card-tags">
          <span v-for="(tag, i) in profile.tags" :key="i" class="tag">{{ tag }}</span>
        </div>
        <div class="profile-card-stats">
          <div class="stat">
            <span class="stat-number">{{ profile.projects }}</span>
            <span class="stat-label">Projects</span>
          </div>
          <div class="stat">
            <span class="stat-number">{{ profile.tasks }}</span>
            <span class="stat-label">Tasks</span>
          </div>
          <div class="stat">
            <span class="stat-number">{{ profile.connections }}</span>
            <span class="stat-label">Connections</span>
          </div>
        </div>
        <div class="profile-card-actions">
          <button @click="changeConnection(index)" class="connect-button">
            {{ profile.connection }}
          </button>
          <button @click="removeProfile(index)" class="delete-button">
            <i class="fa-regular fa-trash-can"></i>
          </button>
          <button class="message-button">
            <i class="fa-regular fa-envelope"></i>
          </button>
        </div>
      </div>
    </div>
    <button @click="addProfile" class="add-profile-button">Add Profile</button>
  </div>
</template>

<script lang="ts">
import { ref } from "vue";

interface Profile {
  avatar: string;
  name: string;
  role: string;
  tags: string[];
  projects: number;
  tasks: string;
  connections: string;
  connection: string;
}

export default {
  setup() {
    const profiles = ref<Profile[]>([
      {
        avatar:
          "https://img.freepik.com/psd-gratis/3d-ilustracion-persona-gafas-sol_23-2149436180.jpg?t=st=1723322273~exp=1723322873~hmac=4725ba2d8db00355d73f9a913d508216f040938e7923d64e9ff73316ac65809e",
        name: "Mark Gilbert",
        role: "UI Designer",
        tags: ["Figma", "Sketch"],
        projects: 18,
        tasks: "834",
        connections: "129",
        connection: "Connect",
      },
      {
        avatar:
          "https://img.freepik.com/psd-gratis/3d-ilustracion-persona-gafas_23-2149436185.jpg?t=st=1723255233~exp=1723255833~hmac=8cfe80a29a689e8a8ca918e1f13f8f1dad559dbec63df56354052deb09e2f5d6",
        name: "Eugenia Parsons",
        role: "Developer",
        tags: ["Angular", "React"],
        projects: 112,
        tasks: "2.31k",
        connections: "1.28k",
        connection: "Connect",
      },
      {
        avatar:
          "https://img.freepik.com/psd-gratis/3d-ilustracion-persona-gafas-sol_23-2149436178.jpg?t=st=1723254812~exp=1723255412~hmac=fcbd12454bea8dc1179b8ec76637ce2c37e6861aa5df3653cc408f08c30a1223",
        name: "Francis Byrd",
        role: "Developer",
        tags: ["HTML", "React"],
        projects: 32,
        tasks: "1.25k",
        connections: "890",
        connection: "Connect",
      },
      {
        avatar:
          "https://img.freepik.com/psd-gratis/3d-ilustracion-persona-cabello-rosado_23-2149436186.jpg?t=st=1723255343~exp=1723255943~hmac=74f2fd4c97abb996f007fcfa87b577d08342b88493d079feccc1f4c74df12258",
        name: "Leon Lucas",
        role: "UI/UX Designer",
        tags: ["Figma", "Sketch", "Photoshop"],
        projects: 86,
        tasks: "12.4k",
        connections: "890",
        connection: "Connect",
      },
      {
        avatar:
          "https://img.freepik.com/psd-gratis/3d-ilustracion-persona-calva_23-2149436183.jpg?t=st=1723322273~exp=1723322873~hmac=d59af65a1bd3e2b9ef020bafc05ee525959c473f26bc112dbab9335bf379f693",
        name: "Jayden Rogers",
        role: "Full Stack Developer",
        tags: ["React", "HTML", "Node.js"],
        projects: 244,
        tasks: "23.8k",
        connections: "2.14k",
        connection: "Connect",
      },
      {
        avatar:
          "https://img.freepik.com/psd-gratis/ilustracion-3d-persona-pelo-punk-chaqueta_23-2149436198.jpg?t=st=1723255512~exp=1723256112~hmac=ad5910375650d0be51937c8d5263f1139b784059f9b81f87485ab5effeda70fe",
        name: "Jeanette Powell",
        role: "SEO",
        tags: ["Analysis", "Writing"],
        projects: 32,
        tasks: "1.28k",
        connections: "1.27k",
        connection: "Connect",
      },
    ]);

    const changeConnection = (index: number) => {
      const profile = profiles.value[index];
      if (profile.connection === "Connect") {
        profile.connection = "Connected";
      } else {
        profile.connection = "Connect";
      }
    };

    const addProfile = () => {
      profiles.value.push({
        avatar:
          "https://img.freepik.com/psd-gratis/ilustracion-3d-persona-sonriente-lentes_23-2149436190.jpg",
        name: "New Profile",
        role: "New Role",
        tags: ["New", "Tags"],
        projects: 0,
        tasks: "0",
        connections: "0",
        connection: "Connect",
      });
    };

    const removeProfile = (index: number) => {
      profiles.value.splice(index, 1);
    };

    return {
      profiles,
      changeConnection,
      addProfile,
      removeProfile,
    };
  },
};
</script>

<style lang="scss">
.profile-cards-container {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 20px;
  padding-top: 20px;
}

.add-profile-button {
  position: fixed;
  bottom: 20px;
  right: 70px;
  background-color: #7f56d9;
  color: #fff;
  border: none;
  border-radius: 5%;
  width: 100px;
  height: 40px;
  font-size: 14px;
  display: flex;
  justify-content: center;
  align-items: center;
  cursor: pointer;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
  transition: background-color 0.3s ease, transform 0.3s ease;

  &:hover {
    background-color: #6842c2;
    transform: scale(1.1);
  }
}

.profile-card {
  background-color: #ffffff;
  border-radius: 8px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
  padding: 20px;
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;

  .profile-card-header {
    display: flex;
    flex-direction: column;
    align-items: center;
    margin-bottom: 10px;

    .avatar {
      width: 80px;
      height: 80px;
      border-radius: 50%;
      margin-bottom: 10px;
    }

    .profile-name {
      font-size: 18px;
      font-weight: 600;
      margin: 0;
    }

    .profile-role {
      font-size: 14px;
      color: #666;
    }
  }

  .profile-card-tags {
    display: flex;
    justify-content: center;
    margin-bottom: 20px;

    .tag {
      background-color: #f0f0f0;
      border-radius: 4px;
      padding: 4px 8px;
      font-size: 12px;
      margin: 0 5px;
    }
  }

  .profile-card-stats {
    display: flex;
    justify-content: space-around;
    width: 100%;
    margin-bottom: 20px;

    .stat {
      display: flex;
      flex-direction: column;
      align-items: center;

      .stat-number {
        font-size: 16px;
        font-weight: 600;
      }

      .stat-label {
        font-size: 12px;
        color: #666;
      }
    }
  }

  .profile-card-actions {
    display: flex;
    justify-content: center;

    .connect-button {
      background-color: #7f56d9;
      color: #fff;
      border: none;
      border-radius: 4px;
      padding: 8px 16px;
      font-size: 14px;
      cursor: pointer;
      transition: background-color 0.3s ease;

      &:hover {
        background-color: #6842c2;
      }
    }

    .delete-button {
      background-color: #dc3545;
      color: #fff;
      border: none;
      border-radius: 4px;
      padding: 8px 16px;
      font-size: 14px;
      cursor: pointer;
      transition: background-color 0.3s ease;
      margin-left: 10px;

      &:hover {
        background-color: #c82333;
      }

      i {
        margin: 0;
      }
    }

    .message-button {
      background-color: #f0f0f0;
      color: #333;
      border: none;
      border-radius: 4px;
      padding: 8px 16px;
      font-size: 14px;
      cursor: pointer;
      transition: background-color 0.3s ease;
      margin-left: 10px;

      &:hover {
        background-color: #e0e0e0;
      }

      i {
        margin: 0;
      }
    }
  }
}
</style>