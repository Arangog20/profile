<template>
  <section class="profile">
    <div class="profile-header">

      <div class="header-background"> </div>

      <div class="profile-details">

        <div class="profile-image">
          <img :src="User.profileImage" alt="Profile Picture" />
        </div>
        
        <div class="profile-info">
          <h1>{{ User.name }}</h1>
          <p class="profile-meta">
            <span class="role"><i class="fa-regular fa-palette" style="width: 2%;padding-right:4%"></i>{{ User.role }}</span>
            <span class="location"><i class="fa-regular fa-location-dot"></i>{{ User.location }}</span>
            <span class="joined-date"><i class="fa-regular fa-calendar" style="width: 50%;padding-right:20%"></i>{{ User.joinedDate }}</span>
            <button @click="change" class="connect-button">
              <span class="connect-icon">🔗</span> {{ connetion }} 
            </button>
          </p>
          
        </div>
       
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { ref } from "vue";
  
  const User = ref({
      profileImage: 'https://img.freepik.com/psd-gratis/ilustracion-3d-persona-gafas-sol-arco-iris_23-2149436181.jpg?t=st=1723255512~exp=1723256112~hmac=07a284abb8397c0f611ba9b3ca886a19f7bd3f57dd17f1e49c56f5e24756f33d',
      name: 'Manuela Arango',
      role: 'Coder',
      location: 'Medellín',
      joinedDate: 'June 2021',
  });

  const connetion = ref<string>('Connect');

  const change = () => {
    if (connetion.value === 'Connect') {
      connetion.value = 'Connected';
    } else {
      connetion.value = 'Connect';
    }
  };

</script>

<style  lang="scss">
.profile{
  display: flex;
  padding-top: 20px;
}

 .profile-header {
  position: relative;
  width: 100%;
  background-color: #fff;
  border-radius: 10px;
  overflow: hidden;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);

  .header-background {
    height: 50%;
    background: linear-gradient(to right, #ff7e5f, #feb47b, #86a8e7, #7f7fd5);
  }

  .profile-details {
    height: 50%;
    display: flex;
    align-items: center;
    padding: 16px;
    padding-top: 2%;
    position: relative;
    top: -50px;

    .profile-image {
      margin-left: 2%;
      width: 10vw;
      height: 20vh;
      border-radius: 5%;
      border: 6px solid #fff;
      overflow: hidden;
      box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
      position: relative;
     

      img {
        width: 100%;
        height: 100%;
        object-fit: cover;
      }
    }

    .profile-info {
      flex-grow: 1;
      margin-left: 16px;
      padding-top: 10%;
      padding-bottom: 1%;

      h1 {
        margin: 0;
        font-size: 24px;
        color: #333;
      }

      .profile-meta {
        display: flex;
        align-items: center;
        margin-top: 8px;
        color: #666;
        font-size: 14px;

        .role,
        .location,
        .joined-date {
          display: inline-flex;
          align-items: center;
          margin-right: 16px;

          &:before {
            content: '';
            width: 16px;
            height: 16px;
            margin-right: 8px;
          }
        }

        
      }
    }

    .connect-button {
      
      display: flex;
      align-items: center;
      background-color: #7f7fd5;
      color: #fff;
      border: none;
      border-radius: 10px;
      padding: 10px 16px;
      font-size: 14px;
      cursor: pointer;
      box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
      position: relative;
      margin-left: 60%;

      .connect-icon {
        margin-right: 8px;
      }
    }
    .connect-button:hover {
  background-color: #9b5c9b;
}
  }
}
</style>

