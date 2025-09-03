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
          }
        });
      }
    });
  });

  // Kur hap faqen → vetëm "Quick Start" hapet
  detailsList.forEach(detail => {
    const summaryText = detail.querySelector("summary")?.textContent.trim();
    if (summaryText === "Quick Start") {
      detail.setAttribute("open", "true");
    } else {
      detail.removeAttribute("open");
    }
  });
});
