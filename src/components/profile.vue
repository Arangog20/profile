<template>
  <div class="dashboard">
    <div class="left-panel">
      <div class="profile-info">
        <h3>About</h3>
        <ul class="no-bullets">
          <li><strong>Full Name:</strong> John Doe</li>
          <li><strong>Status:</strong> Active</li>
          <li><strong>Role:</strong> Developer</li>
          <li><strong>Country:</strong> COL</li>
          <li><strong>Language:</strong> English</li>
        </ul>
        <h3>Contacts</h3>
        <ul class="no-bullets">
          <li><i class="fas fa-phone"></i> <strong>Contact:</strong> (123) 456-7890</li>
          <li><i class="fab fa-skype"></i> <strong>Skype:</strong> john.doe</li>
          <li><i class="fas fa-envelope"></i> <strong>Email:</strong> john.doe@example.com</li>
        </ul>
        <h3>Teams</h3>
        <ul class="no-bullets">
          <li><i class="fas fa-users"></i> Backend Developer (126 Members)</li>
          <li><i class="fas fa-code"></i> VueJS Developer (98 Members)</li>
        </ul>
      </div>
      
      <div class="overview">
        <h3>Overview</h3>
        <ul class="no-bullets">
          <li><strong>Task Completed:</strong> 13.5k</li>
          <li><strong>Connections:</strong> 897</li>
          <li><strong>Projects Compiled:</strong> 146</li>
        </ul>
      </div>
    </div>

    
    <div class="right-panel">
     
      <div class="activity-timeline">
        <h3>Activity Timeline</h3>
        <ul>
          <li>
            <div class="activity-item">
              <p><i class="fas fa-file-invoice"></i> 12 Invoices have been paid</p>
              <a href="#" class="invoice-link">Invoice.pdf</a>
              <span class="timestamp">12 min ago</span>
            </div>
          </li>
          <li>
            <div class="activity-item">
              <p><i class="fas fa-calendar-alt"></i> Project meeting with John @10:15am</p>
              <span class="timestamp">45 min ago</span>
            </div>
          </li>
          <li>
            <div class="activity-item">
              <p><i class="fas fa-plus-circle"></i> Create a new project for client</p>
              <div class="avatar-group">
                <img v-for="n in 5" :key="n" :src="`/avatars/avatar${n}.png`" class="avatar" />
                <span class="extra-avatars">+3</span>
              </div>
              <span class="timestamp">2 days ago</span>
            </div>
          </li>
        </ul>
      </div>

      
      <div class="cards-container">
        
        <div class="connections-card">
          <h3>Connection</h3>
          <ul>
            <li v-for="connection in connections" :key="connection.id" class="connection-item">
              <img :src="connection.avatar" class="connection-avatar" />
              <div>
                <p>{{ connection.name }}</p>
                <span>{{ connection.count }} Connections</span>
              </div>
              <button class="connect-btn"><i class="fas fa-user-plus"></i></button>
            </li>
          </ul>
          <a href="#" class="view-link">View all connections</a>
        </div>

        
        <div class="teams-card">
          <h3>Teams</h3>
          <ul>
            <li v-for="team in teams" :key="team.id" class="team-item">
              <div>
                <p>{{ team.name }}</p>
                <span>{{ team.members }} Members</span>
              </div>
              <span class="badge">{{ team.role }}</span>
            </li>
          </ul>
          <a href="#" class="view-link">View all Teams</a>
        </div>
      </div>

      
      <div class="project-list">
        <h3>Project List</h3>
        <table>
          <thead>
            <tr>
              <th>Project</th>
              <th>Leader</th>
              <th>Team</th>
              <th>Progress</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="project in projects" :key="project.id">
              <td>
                <img :src="project.icon" class="project-icon" />
                {{ project.name }}
              </td>
              <td>{{ project.leader }}</td>
              <td>{{ project.team }}</td>
              <td>
                <div class="progress-bar-container">
                  <div class="progress-bar" :style="{ width: project.progress + '%' }"></div>
                </div>
                <span>{{ project.progress }}%</span>
              </td>
            </tr>
          </tbody>
        </table>
        <div class="pagination">
          <button @click="previousPage"><i class="fas fa-arrow-left"></i></button>
          <button @click="nextPage"><i class="fas fa-arrow-right"></i></button>
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  data() {
    return {
      connections: [
        { id: 1, name: 'Cecilia Payne', count: 45, avatar: 'https://img.freepik.com/psd-gratis/3d-ilustracion-persona-gafas-sol_23-2149436180.jpg?t=st=1723322273~exp=1723322873~hmac=4725ba2d8db00355d73f9a913d508216f040938e7923d64e9ff73316ac65809e' },
        { id: 2, name: 'Curtis Fletcher', count: 1320, avatar: 'https://img.freepik.com/psd-gratis/3d-ilustracion-persona-gafas-sol_23-2149436188.jpg?t=st=1723255512~exp=1723256112~hmac=b081d324b078fcbce54eb12e63c35bdf8f130aa683053c4fa150f8bd13dfba21' },
        { id: 3, name: 'Alice Stone', count: 125, avatar: 'https://img.freepik.com/psd-gratis/3d-ilustracion-persona-cabello-rosado_23-2149436186.jpg?t=st=1723255343~exp=1723255943~hmac=74f2fd4c97abb996f007fcfa87b577d08342b88493d079feccc1f4c74df12258' },
        { id: 4, name: 'Darrell Barnes', count: 456, avatar: 'https://img.freepik.com/psd-gratis/3d-ilustracion-persona_23-2149436192.jpg?w=826&t=st=1723254812~exp=1723255412~hmac=a7fd36b7653e8325a5c3e82e6d11814f913d4a154f8fc5c821052aed723dd0e2' },
        { id: 5, name: 'Eugenia Moore', count: 1200, avatar: 'https://img.freepik.com/psd-gratis/3d-ilustracion-persona-gafas_23-2149436185.jpg?t=st=1723255233~exp=1723255833~hmac=8cfe80a29a689e8a8ca918e1f13f8f1dad559dbec63df56354052deb09e2f5d6' }
      ],
      teams: [
        { id: 1, name: 'React Developers', members: 72, role: 'Developer' },
        { id: 2, name: 'Support Team', members: 122, role: 'Support' },
        { id: 3, name: 'UI Designer', members: 45, role: 'Designer' },
        { id: 4, name: 'VueJS Developers', members: 289, role: 'Developer' },
        { id: 5, name: 'Digital Marketing', members: 24, role: 'Marketing' }
      ],
      projects: [
        { id: 1, name: 'BGC eCommerce App', leader: 'Eileen', team: 'React Project', progress: 78, icon: 'https://www.freecodecamp.org/news/content/images/2022/02/image-76.png' },
        { id: 2, name: 'Falcon Logo Design', leader: 'Owen', team: 'Figma Project', progress: 25, icon: 'https://w7.pngwing.com/pngs/911/515/png-transparent-figma-logo-brand-logos-brands-in-colors-icon.png' },
        { id: 3, name: 'Dashboard Design', leader: 'Keith', team: 'VueJS Project', progress: 62, icon: 'https://w7.pngwing.com/pngs/980/549/png-transparent-vuejs-original-logo-icon.png' },
        { id: 4, name: 'Foodista mobile app', leader: 'Merline', team: 'Xamarin Project', progress: 61, icon: 'https://movilion.com/wp-content/uploads/2016/12/xamarin.png' },
        { id: 5, name: 'Dojo Email App', leader: 'Harmonia', team: 'Python Project', progress: 51, icon: 'https://i0.wp.com/junilearning.com/wp-content/uploads/2020/06/python-programming-language.webp?resize=800%2C800&ssl=1' }
      ]
    };
  },
 
});
</script>

<style lang="scss" scoped>
body{
  color:#c1c1c2;
}

.dashboard {
  display: flex;
  gap: 20px;
  padding: 20px;
  font-family: 'Arial', sans-serif;
}

.left-panel {
  flex: 1;
  display: flex;
  flex-direction: column;
  gap: 20px;
}

.right-panel {
  flex: 2;
  display: flex;
  flex-direction: column;
  gap: 20px;
}

.profile-info,
.contacts,
.teams,
.overview,
.activity-timeline,
.connections-card,
.teams-card,
.project-list {
  background: #ffffff;
  padding: 10px;
  border-radius: 10px;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
}

.activity-timeline ul,
.connections-card ul,
.teams-card ul {
  list-style: none;
  padding: 0;
  margin: 0;
}

.activity-item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 10px 0;
}

.activity-item p {
  display: flex;
  align-items: center;
  gap: 10px;
}

.avatar-group {
  display: flex;
  align-items: center;
  gap: 5px;
}

.avatar {
  width: 30px;
  height: 30px;
  border-radius: 50%;
  object-fit: cover;
}

.extra-avatars {
  background: #e2e8f0;
  border-radius: 50%;
  padding: 5px;
  font-size: 12px;
  text-align: center;
  line-height: 20px;
}

.connection-item {
  display: flex;
  align-items: center;
  gap: 15px;
  margin-bottom: 10px;
}

.connection-avatar {
  width: 50px;
  height: 50px;
  border-radius: 50%;
  object-fit: cover;
}

.connect-btn {
  background: #5a67d8;
  border: none;
  padding: 5px 10px;
  border-radius: 5px;
  color: white;
  cursor: pointer;
}

.team-item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 10px 0;
}

.badge {
  background: #5a67d8;
  color: white;
  padding: 5px 10px;
  border-radius: 5px;
}

.project-list table {
  width: 100%;
  border-collapse: collapse;
  margin-top: 10px;
}

.project-list th,
.project-list td {
  padding: 10px;
  text-align: left;
}

.project-list th {
  background-color: #f7f7f7;
  font-weight: normal;
}

.project-list td {
  border-bottom: 1px solid #eaeaea;
}

.project-icon {
  width: 24px;
  height: 24px;
  margin-right: 10px;
}

.progress-bar-container {
  background: #e2e8f0;
  border-radius: 5px;
  height: 10px;
  width: 100%;
  margin-top: 5px;
}

.progress-bar {
  height: 100%;
  background-color: #48bb78;
  border-radius: 5px;
}

.pagination {
  display: flex;
  justify-content: space-between;
  margin-top: 20px;
}

.cards-container {
  display: flex;
  gap: 20px;
}

a.view-link {
  color: #5a67d8;
  text-decoration: none;
  font-weight: bold;
  margin-top: 10px;
  display: inline-block;
}

a.view-link:hover {
  text-decoration: underline;
}

.invoice-link {
  color: #e53e3e;
  text-decoration: none;
  font-size: 14px;
}

.invoice-link:hover {
  text-decoration: underline;
}

.timestamp {
  font-size: 12px;
  color: #a0aec0;
}
.no-bullets {
  list-style-type: none;
  padding-left: 0;
}
</style>