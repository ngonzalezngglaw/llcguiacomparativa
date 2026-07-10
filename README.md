<script>
    document.addEventListener('DOMContentLoaded', () => {
        const observerOptions = {
            root: null,
            rootMargin: '0px',
            threshold: 0.15
        };

        const observer = new IntersectionObserver((entries, observer) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.classList.add('visible');
                    observer.unobserve(entry.target);
                }
            });
        }, observerOptions);

        // Activa las animaciones de subida en los elementos compatibles
        document.querySelectorAll('.fade-up').forEach((elem) => {
            observer.observe(elem);
        });

        // Efecto premium de desenfoque (blur) en la barra de navegación al hacer scroll
        const navbar = document.getElementById('navbar');
        if (navbar) {
            window.addEventListener('scroll', () => {
                if (window.scrollY > 50) {
                    navbar.style.background = 'rgba(3, 7, 18, 0.85)';
                    navbar.style.boxShadow = '0 10px 30px rgba(0,0,0,0.5)';
                } else {
                    navbar.style.background = 'rgba(3, 7, 18, 0.7)';
                    navbar.style.boxShadow = 'none';
                }
            });
        }
    });
</script>
