document.addEventListener('DOMContentLoaded', () => {
  const navItems = document.querySelectorAll("nav summary, nav ul li a");
  const detailsList = document.querySelectorAll("nav details");

  // ruaj nav-active
  navItems.forEach(item => {
    item.addEventListener("click", () => {
      navItems.forEach(el => el.classList.remove('nav-active'));
      item.classList.add('nav-active');
    });
  });

  // Accordion behavior → hap vetëm një details
  detailsList.forEach(detail => {
    detail.addEventListener("toggle", () => {
      if (detail.open) {
        detailsList.forEach(other => {
          if (other !== detail) {
            other.removeAttribute("open");
            other.querySelector("summary")?.classList.remove("nav-active");
          }
        });
        // vendos ngjyrën blu summary kur hapet
        detail.querySelector("summary")?.classList.add("nav-active");
      } else {
        detail.querySelector("summary")?.classList.remove("nav-active");
      }
    });
  });

  // Kur hap faqen → vetëm "Quick Start" hapet dhe ka ngjyrë
  detailsList.forEach(detail => {
    const summary = detail.querySelector("summary");
    const summaryText = summary?.textContent.trim();
    if (summaryText === "Quick Start") {
      detail.setAttribute("open", "true");
      summary?.classList.add("nav-active");
    } else {
      detail.removeAttribute("open");
      summary?.classList.remove("nav-active");
    }
  });
});
