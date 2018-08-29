<template>
<div id="experience">
<span v-for="pos in positions">
    <h3><b>{{ pos.title }}</b></h3>
    <h3>{{ pos.company }}</h3>
    <ul>
        <li><b>{{ pos.location }}</b></li>
        <li><b>{{ pos.period }}</b></li>
        <li><b>Tech: </b>{{ pos.tech }}</li>
        <li><b>Projects:</b>
            <ul>
                <li v-for="proj in pos.projects">
                    {{ proj }}
                </li>
            </ul>
        </li>
    </ul>
</span>
</div>
</template>

<script>
export default {
  name: "Experience",
  data() {
    return {
      positions: [
        {
          title: "Backend Engineer",
          company: "GetStream.io",
          location: "Amsterdam",
          period: "2017 - present",
          tech:
            "Go, Python, AWS, Postgres, Redis, Puppet, ReactJS, Django, RabbitMQ",
          projects: [
            "Migration from old python based infrastructure to new go based one (Backend)",
            "Migration tool for switching datacenters for an app (Backend)",
            "Import data into existing app (Backend + Frontend)",
            "Audit log for all API calls (Backend + Frontend)",
            "Various other small features and improvements (Backend + Frontend)"
          ]
        },
        {
          title: " Software Engineer",
          company: "Verint Systems",
          location: "Zoetermeer",
          period: "2016 - 2017",
          tech:
            "C++, Python, Perl, Javascript, MongoDB, MySQL, Qt5, Debian packaging, Docker, RabbitMQ, ZMQ",
          projects: [
            "Licensing server (Backend)",
            "Audit logs (Frontend + Backend)",
            "Permission system (Frontend + Backend)",
            "Map viewer (Frontend)",
            "Deployment server (Backend)",
            "Various other small features and improvements (Backend + Frontend)"
          ]
        },
        {
          title: "Senior Software Engineer",
          company: "Telenav",
          location: "Cluj-Napoca",
          period: "2014 - 2016",
          tech: "C++11, Cross-Platform, nginx, GPX",
          projects: [
            "GPX Library",
            "Delta updates (minutely map updates)",
            "Map Advisor",
            "Map package manager",
            "Map update compacter",
            "Routing server"
          ]
        },
        {
          title: "Junior Software Engineer",
          company: "Temasoft",
          location: "Cluj-Napoca",
          period: "2012 - 2014",
          tech: "C++11, C#, .NET, MSSQL, Microsoft Server 2012, WiX, WinPCAP",
          projects: ["WebMonitor Proxy", "WebMonitor Agent", "WebMonitor DAL"]
        }
      ]
    };
  }
};
</script>
