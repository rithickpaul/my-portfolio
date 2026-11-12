
// ======================================
// RITHICK PAUL - PORTFOLIO INTERACTIONS
// ======================================

// MOBILE NAVIGATION

const menuToggle = document.getElementById("menu-toggle");
const navLinks = document.getElementById("nav-links");

if (menuToggle && navLinks) {
    menuToggle.addEventListener("click", () => {
        navLinks.classList.toggle("active");
    });

    document.querySelectorAll(".nav-links a").forEach(link => {
        link.addEventListener("click", () => {
            navLinks.classList.remove("active");
        });
    });
}

// COPYRIGHT YEAR

const year = document.getElementById("year");

if (year) {
    year.textContent = new Date().getFullYear();
}

// LIVE ANIMATED BACKGROUND

const ambient = document.createElement("div");
ambient.className = "ambient-background";
ambient.setAttribute("aria-hidden", "true");




ambient.innerHTML = `
    <div class="gradient-orb orb-purple"></div>
    <div class="gradient-orb orb-pink"></div>
    <div class="gradient-orb orb-cyan"></div>
    <div class="particle-container"></div>
    <div class="mouse-glow"></div>


<div class="floating-3d sphere sphere-one"></div>
<div class="floating-3d sphere sphere-two"></div>
<div class="floating-3d ring ring-one"></div>
<div class="floating-3d ring ring-two"></div>
<div class="floating-3d crystal"></div>
`;

document.body.prepend(ambient);

// GENERATE FLOATING PARTICLES

const particleContainer = ambient.querySelector(".particle-container");

for (let i = 0; i < 110; i++) {
    const particle = document.createElement("span");

    particle.className = "particle";

    const size = Math.random() * 3 + 1;

    particle.style.left = Math.random() * 100 + "%";
    particle.style.top = Math.random() * 100 + "%";
    particle.style.width = size + "px";
    particle.style.height = size + "px";
    particle.style.setProperty(
        "--duration",
        (Math.random() * 12 + 8) + "s"
    );
    particle.style.setProperty(
        "--delay",
        (Math.random() * -20) + "s"
    );

    particleContainer.appendChild(particle);
}

// MOUSE FOLLOWING GLOW

const mouseGlow = ambient.querySelector(".mouse-glow");

if (window.matchMedia("(pointer: fine)").matches) {
    document.addEventListener("mousemove", (event) => {
        mouseGlow.style.left = event.clientX + "px";
        mouseGlow.style.top = event.clientY + "px";
    });
}

// SCROLL REVEAL ANIMATIONS

const revealElements = document.querySelectorAll(
    ".hero-content, .hero-card, .section, .skill-card, .project-card, .contact-card"
);

revealElements.forEach(element => {
    element.classList.add("reveal");
});

if ("IntersectionObserver" in window) {
    const observer = new IntersectionObserver((entries) => {
        entries.forEach(entry => {
            if (entry.isIntersecting) {
                entry.target.classList.add("visible");
                observer.unobserve(entry.target);
            }
        });
    }, {
        threshold: 0.12
    });

    revealElements.forEach(element => observer.observe(element));
} else {
    revealElements.forEach(element => element.classList.add("visible"));
}

console.log("Rithick's futuristic portfolio loaded successfully!");

// TYPING ANIMATION

const typingText = document.getElementById("typing-text");

if (typingText) {
    const roles = [
        "Aspiring Software Developer",
        "Python & Java Programmer",
        "C/C++ Developer",
        "Hackathon Enthusiast"
    ];

    let roleIndex = 0;
    let charIndex = roles[0].length;
    let deleting = true;

    const reducedMotion = window.matchMedia(
        "(prefers-reduced-motion: reduce)"
    ).matches;

    if (!reducedMotion) {
        function typeEffect() {
            const currentRole = roles[roleIndex];

            if (deleting) {
                charIndex--;
            } else {
                charIndex++;
            }

            typingText.textContent =
                currentRole.substring(0, charIndex);

            let delay = deleting ? 45 : 85;

            if (charIndex === 0) {
                deleting = false;
                roleIndex = (roleIndex + 1) % roles.length;
                delay = 400;
            }

            if (charIndex === roles[roleIndex].length && !deleting) {
                deleting = true;
                delay = 1600;
            }

            setTimeout(typeEffect, delay);
        }

        setTimeout(typeEffect, 1600);
    }
}

/* =================================
   INTERACTIVE 3D MOUSE TILT EFFECT
================================= */

const tiltCards = document.querySelectorAll(
    ".skill-card, .project-card"
);

const canHover = window.matchMedia("(hover: hover) and (pointer: fine)").matches;

if (canHover && !window.matchMedia("(prefers-reduced-motion: reduce)").matches) {
    tiltCards.forEach(card => {
        card.addEventListener("mousemove", (event) => {
            const rect = card.getBoundingClientRect();

            const x = event.clientX - rect.left;
            const y = event.clientY - rect.top;

            const centerX = rect.width / 2;
            const centerY = rect.height / 2;

            const rotateX = ((y - centerY) / centerY) * -8;
            const rotateY = ((x - centerX) / centerX) * 8;

            card.style.transform = `
                perspective(900px)
                rotateX(${rotateX}deg)
                rotateY(${rotateY}deg)
                translateY(-8px)
                scale(1.025)
            `;
        });

        card.addEventListener("mouseleave", () => {
            card.style.transform = "";
        });
    });
}

/* =================================
   INTERACTIVE CURSOR GLOW
================================= */

document.addEventListener("mousemove", (event) => {
    document.documentElement.style.setProperty(
        "--mouse-x",
        event.clientX + "px"
    );

    document.documentElement.style.setProperty(
        "--mouse-y",
        event.clientY + "px"
    );
});
