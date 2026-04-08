<script setup>
const config = useRuntimeConfig()
const resumeUrl = `${config.app.baseURL}files/Shlok_Shinde_SWE_Resume.pdf`
</script>

<template>
<div>
    <img class="w-44 h-44 object-cover rounded-sm mb-4 border border-gray-300" src="@/assets/Biography/self.jpg" alt="Shlok Shinde profile photo" />
    <h2 class="font-bold text-2xl py-5">Shlok Shinde</h2>
    <h4 class="text-gray-600 font-medium text-xs" style="padding-bottom: 10px">
        Software Engineer • Product Manager • AI Developer
    </h4>
    <h4 class="text-gray-600 font-medium text-xs">Knoxville, TN 📍</h4>

    <div class="flex flex-wrap mt-5 gap-2 items-center">
        <img class="w-auto h-5 rounded-none text-xs" alt="Python" src="https://img.shields.io/badge/-Python-blue" />
        <img class="w-auto h-5 rounded-none text-xs" alt="PHP" src="https://img.shields.io/badge/-PHP-777BB4" />
        <img class="w-auto h-5 rounded-none text-xs" alt="JavaScript" src="https://img.shields.io/badge/-Javascript-yellow" />
        <img class="w-auto h-5 rounded-none text-xs" alt="C++" src="https://img.shields.io/badge/-C%2B%2B-00599C" />
        <img class="w-auto h-5 rounded-none text-xs" alt="SQL" src="https://img.shields.io/badge/-SQL-lightgrey" />
        <img class="w-auto h-5 rounded-none text-xs" alt="Git" src="https://img.shields.io/badge/-Git-critical" />
        <img class="w-auto h-5 rounded-none text-xs" alt="React" src="https://img.shields.io/badge/-React-61DAFB" />
        <img class="w-auto h-5 rounded-none text-xs" alt="Next.js" src="https://img.shields.io/badge/-Next.js-black" />
        <img class="w-auto h-5 rounded-none text-xs" alt="FastAPI" src="https://img.shields.io/badge/-FastAPI-009688" />
        <img class="w-auto h-5 rounded-none text-xs" alt="PyTorch" src="https://img.shields.io/badge/-PyTorch-EE4C2C" />
        <img class="w-auto h-5 rounded-none text-xs" alt="TensorFlow" src="https://img.shields.io/badge/-TensorFlow-FF6F00" />
        <img class="w-auto h-5 rounded-none text-xs" alt="OpenCV" src="https://img.shields.io/badge/-OpenCV-5C3EE8" />
        <img class="w-auto h-5 rounded-none text-xs" alt="Figma" src="https://img.shields.io/badge/-Figma-8c5aee" />
    </div>

    <div class="pt-7">
        <h3 class="underline font-bold text-md pb-1">About Me</h3>
        <p class="font-thin text-sm pb-2.5">
            I am a Computer Science student at the University of Tennessee, Knoxville focused on software engineering, AI systems, and full-stack product development.
        </p>
        <p class="font-thin text-sm pb-2.5">
            I enjoy building practical systems that connect strong backend architecture with user-facing impact, from lead automation workflows to research-driven computer vision pipelines.
        </p>
        <p class="font-thin text-sm pb-2.5">
            Outside of coding, I lead technical teams, mentor collaborators, and continuously explore modern AI and cloud workflows.
        </p>
    </div>

    <div class="pt-7">
        <h3 class="underline font-bold text-md pb-1">What I'm Into Right Now</h3>
        <ul class="list-disc pl-5 mt-2 space-y-1 text-sm font-thin">
            <li>Building cool things with AI and full-stack tools.</li>
            <li>Curating playlists for literally every mood.</li>
            <li>Mixing creativity and engineering in everything I work on.</li>
        </ul>
    </div>

    <div class="pt-7">
        <h3 class="underline font-bold text-md pb-1">Non-Tech Things About Me</h3>
        <div class="hobby-grid pt-2">
            <div class="hobby-card">
                <img class="hobby-icon" src="@/assets/win95Icons/dj.svg" alt="DJ icon" />
                <p class="hobby-title">DJ</p>
                <p class="hobby-copy">I DJ and love reading a room through music.</p>
            </div>
            <div class="hobby-card">
                <img class="hobby-icon" src="@/assets/win95Icons/guitar.svg" alt="Guitar icon" />
                <p class="hobby-title">Guitar</p>
                <p class="hobby-copy">I play guitar and enjoy experimenting with riffs and sounds.</p>
            </div>
            <div class="hobby-card">
                <img class="hobby-icon" src="@/assets/win95Icons/pickleball.svg" alt="Pickleball icon" />
                <p class="hobby-title">Pickleball</p>
                <p class="hobby-copy">I play pickleball for fun and competition.</p>
            </div>
            <div class="hobby-card">
                <img class="hobby-icon" src="@/assets/win95Icons/music.svg" alt="Music icon" />
                <p class="hobby-title">Music</p>
                <p class="hobby-copy">Music is a huge part of my life, on and off the laptop.</p>
            </div>
        </div>
    </div>

    <div class="pt-7">
        <h3 class="underline font-bold text-md pb-1">Work Experience</h3>
    </div>

    <section class="pt-6">
        <h4 class="text-lg font-semibold">LaRevela</h4>
        <p class="text-gray-600 text-xs">Agentic AI Developer • Jan 2026 – Present • Franklin, TN</p>
        <ul class="list-disc pl-5 mt-2 space-y-1 text-sm font-thin">
            <li>Architected an AI-driven lead engagement backend using Python, FastAPI, and MySQL.</li>
            <li>Built asynchronous Gmail-to-OpenAI workflows with sub-1 minute lead response latency.</li>
            <li>Integrated Calendly scheduling flows that increased demo booking conversion by 35%.</li>
            <li>Optimized high-volume email thread processing by 30%.</li>
        </ul>
    </section>

    <section class="pt-6">
        <h4 class="text-lg font-semibold">Hack4Impact</h4>
        <p class="text-gray-600 text-xs">Product Manager • Sep 2025 – Present • Knoxville, TN</p>
        <ul class="list-disc pl-5 mt-2 space-y-1 text-sm font-thin">
            <li>Led a 9-person team building a React/Next.js/PostgreSQL platform.</li>
            <li>Replaced paid software and reduced annual costs by about $6,000.</li>
            <li>Defined architecture and roadmap with focus on scalability and maintainability.</li>
            <li>Improved deployment velocity by 15% through Agile and CI/CD workflows.</li>
        </ul>
    </section>

    <section class="pt-6">
        <h4 class="text-lg font-semibold">University of Tennessee, Knoxville</h4>
        <p class="text-gray-600 text-xs">Undergraduate Research Assistant • Aug 2025 – Jan 2026 • Knoxville, TN</p>
        <ul class="list-disc pl-5 mt-2 space-y-1 text-sm font-thin">
            <li>Built a computer vision pipeline using PyTorch, TensorFlow, and YOLO.</li>
            <li>Achieved 84% re-identification accuracy on multi-frame datasets.</li>
            <li>Reduced manual labeling effort by 30% through automated identity tracking.</li>
        </ul>
    </section>

    <section class="pt-6">
        <h4 class="text-lg font-semibold">LeadsPedia, Inc.</h4>
        <p class="text-gray-600 text-xs">Software Engineer Intern • May 2025 – Aug 2025 • Franklin, TN</p>
        <ul class="list-disc pl-5 mt-2 space-y-1 text-sm font-thin">
            <li>Developed an internal HR platform with PHP, MySQL, and JavaScript.</li>
            <li>Implemented RBAC and session authentication for secure access.</li>
            <li>Built audit-friendly schemas with soft deletes across core workflows.</li>
            <li>Delivered features across 8+ Agile sprints while reducing technical debt.</li>
        </ul>
    </section>

    <div class="pt-10">
        <h3 class="underline font-bold text-md pb-1">Projects & Achievements</h3>
    </div>

    <div class="pt-7">
        <div>
            <h3 class="pb-1"><b>Droplet Tracking</b></h3>
            <h6 class="text-gray-600 font-medium text-xs">Computer Vision Research Project</h6>
            <p class="font-thin text-sm pb-2.5">
                Built a Python/OpenCV/NumPy workflow to track and analyze water droplets in a vertical wind tunnel for fluid dynamics analysis.
            </p>
        </div>

        <div class="pt-7">
            <h3 class="pb-1"><b>Threat Intelligence Aggregator</b></h3>
            <h6 class="text-gray-600 font-medium text-xs">Cybersecurity News Aggregator</h6>
            <p class="font-thin text-sm pb-2.5">
                Created a Python web scraping tool that aggregates daily cybersecurity news into one stream for faster monitoring.
            </p>
        </div>
        
        <div class="pt-7">
            <h3 class="pb-1"><b>Hack4Impact Platform</b></h3>
            <h6 class="text-gray-600 font-medium text-xs">Full-Stack Product Leadership</h6>
            <p class="font-thin text-sm pb-2.5">
                Led architecture and delivery of a React, Next.js, and PostgreSQL platform that replaced paid tools and reduced annual operating costs.
            </p>
        </div>

        <div class="pt-7">
            <h3 class="pb-1"><b>Leadership & Community</b></h3>
            <h6 class="text-gray-600 font-medium text-xs">Ongoing Involvement</h6>
            <p class="font-thin text-sm pb-2.5">
                Active in Hack4Impact, Indian American Association, and Management Society while building collaborative software projects.
            </p>
        </div>
    </div>

    <div class="pt-7">
        <h3 class="pb-1"><b>Résumé</b></h3>
        <a style="color: #ff5733" :href="resumeUrl" class="font-thin text-sm pb-2.5">Check out my résumé here.</a>
    </div>
</div>
</template>

<style scoped>
.hobby-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(170px, 1fr));
    gap: 10px;
}

.hobby-card {
    border-top: solid rgb(250, 250, 250) 1.5px;
    border-left: solid rgb(250, 250, 250) 1.5px;
    border-bottom: solid rgb(90, 90, 90) 1.5px;
    border-right: solid rgb(90, 90, 90) 1.5px;
    background: rgb(192, 192, 192);
    box-shadow: 1px 1px black;
    padding: 10px;
}

.hobby-icon {
    width: 40px;
    height: 40px;
    object-fit: contain;
}

.hobby-title {
    font-weight: 700;
    font-size: 13px;
    margin-top: 6px;
}

.hobby-copy {
    font-size: 12px;
    font-weight: 300;
    margin-top: 4px;
    line-height: 1.3;
}
</style>
