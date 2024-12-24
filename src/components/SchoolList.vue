<template>
  <div class="school-list-container">
    <!-- Banner Section -->
    <header class="banner-section">
      <img src="/banner (1).png" alt="WizFit Challenge Banner" class="banner-image" />
    </header>

    <!-- Intro Section -->
    <section class="intro-section">
      <div class="intro-header">
        <h1>What is WizFit Challenge?</h1>
        <button class="watch-video-button">Watch Video</button>
      </div>
    </section>

    <!-- Player Section -->
    <section class="player-section">
      <img src="/player.png" alt="Player Promoting WizFit Challenge" class="player-image" />
    </section>

    <!-- Challenge Box -->
    <section class="challenge-section">
      <div class="challenge-box">
        <h2 class="challenge-heading">Are you ready to take the challenge?</h2>
        <p class="download-text">Download Harlem Wizards App</p>
        <div class="download-buttons">
          <img src="/goolge-store.png" alt="Google Play Store" class="store-button" loading="lazy" />
          <img src="/apple-store.png" alt="App Store" class="store-button" loading="lazy" />
        </div>
        <p class="sign-up-text">
          <span class="line"></span>
          or you can sign up right now
          <span class="line"></span>
        </p>
        <input
          v-model="searchQuery"
          @input="fetchSchools"
          type="text"
          placeholder="Search Campaign here..."
          class="search-box"
        />
        <ul v-if="schools.length" class="campaign-list">
          <li v-for="school in schools" :key="school.id" class="campaign-card">
            <div class="campaign-info">
              <img
                v-if="school.logo_url"
                :src="school.logo_url"
                alt="School Logo"
                class="school-logo"
                loading="lazy"
              />
              <h3 class="school-name">{{ school.school_name }}</h3>
            </div>
            <button class="join-button">Join Campaign</button>
          </li>
        </ul>
        <p v-else class="no-results">No schools found.</p>
      </div>
    </section>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "SchoolList",
  data() {
    return {
      searchQuery: "",
      schools: [],
    };
  },
  methods: {
    async fetchSchools() {
      try {
        const { data } = await axios.get(
          "https://api.devharlemwizardsinabox.com/campaign/campaign_school_list/",
          {
            params: { search: this.searchQuery },
          }
        );
        this.schools = data.school_list || [];
      } catch (error) {
        console.error("Error fetching schools:", error);
        this.schools = [];
      }
    },
  },
  mounted() {
    this.fetchSchools();
  },
};
</script>

<style scoped>
/* General Container */
.school-list-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  background-color: #f7f7f7;
  padding: 20px;
}

/* Banner Section */
.banner-section {
  width: 100%;
  margin-bottom: 20px;
}

.banner-image {
  width: 100%;
  height: auto;
  display: block;
}

/* Intro Section */
.intro-header {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 20px;
  margin-bottom: 30px;
  flex-wrap: wrap;
  text-align: center;
}

.intro-header h1 {
  font-size: 36px;
  font-weight: bold;
  color: #d92332;
}

.watch-video-button {
  background-color: #ff5c5c;
  color: white;
  border: none;
  padding: 12px 24px;
  font-size: 18px;
  border-radius: 6px;
  cursor: pointer;
  transition: background-color 0.3s;
}

.watch-video-button:hover {
  background-color: #e64545;
}

/* Player Section */
.player-section {
  text-align: center;
  margin-bottom: -60px;
}

.player-image {
  width: 80%; /* Responsive width */
  max-width: 300px; /* Max size for larger screens */
  height: auto;
}

/* Challenge Box */
.challenge-box {
  background-color: #ffffff;
  border: 1px solid #ddd;
  border-radius: 10px;
  padding: 30px;
  width: 100%;
  max-width: 600px;
  text-align: center;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}

.challenge-heading {
  font-size: 28px;
  color: #d92332;
  margin-bottom: 15px;
}

.download-text {
  font-size: 20px;
  color: #555;
  margin-bottom: 25px;
}

.download-buttons {
  display: flex;
  justify-content: center;
  gap: 15px;
}

.store-button {
  width: 120px; /* Reduced size for smaller screens */
  max-width: 160px;
}

.sign-up-text {
  font-size: 16px;
  color: #555;
  margin-bottom: 25px;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 10px;
  text-align: center;
  flex-wrap: wrap;
}

.line {
  flex: 1;
  height: 1px;
  background-color: #d3d3d3;
}

/* Search Box */
.search-box {
  width: 90%;
  max-width: 500px;
  padding: 14px;
  font-size: 18px;
  border: 1px solid #ddd;
  border-radius: 8px;
  background-color: #fff;
  margin-bottom: 30px;
}

/* Campaign List */
.campaign-list {
  list-style: none;
  padding: 0;
  margin: 0;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 15px;
}

.campaign-card {
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 90%;
  max-width: 500px;
  padding: 10px;
  background-color: #f9f9f9;
  border: 1px solid #ddd;
  border-radius: 10px;
  transition: box-shadow 0.2s;
}

.campaign-card:hover {
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.15);
}

.campaign-info {
  display: flex;
  align-items: center;
  gap: 15px;
}

.school-logo {
  width: 60px;
  height: 60px;
  border-radius: 50%;
  object-fit: cover;
}

.school-name {
  font-size: 18px;
  font-weight: bold;
  color: #333;
}

.join-button {
  background-color: #fff;
  color: #d92332;
  padding: 10px 20px;
  font-size: 16px;
  border: 1px solid #d92332;
  border-radius: 6px;
  font-weight: bold;
  cursor: pointer;
  transition: background-color 0.3s, color 0.3s;
}

.join-button:hover {
  background-color: #d92332;
  color: #fff;
}

/* No Results */
.no-results {
  font-size: 18px;
  color: #888;
  margin-top: 20px;
}

/* Responsive Design */
@media (max-width: 768px) {
  .intro-header h1 {
    font-size: 28px;
  }

  .watch-video-button {
    font-size: 16px;
    padding: 10px 20px;
  }

  .player-image {
    width: 100%;
  }

  .challenge-box {
    padding: 20px;
  }

  .download-buttons img {
    width: 100px;
  }

  .campaign-card {
    padding: 8px;
  }

  .school-logo {
    width: 50px;
    height: 50px;
  }

  .join-button {
    font-size: 14px;
    padding: 8px 15px;
  }
}
</style>
