# challenge-amigo-secreto_esp-main
const amigos = [];

document.addEventListener("DOMContentLoaded", () => {
    document.getElementById("btnAgregar").addEventListener("click", agregarAmigo);
    document.getElementById("btnSortear").addEventListener("click", sortearAmigo);
    
    // Detectar "Enter" en el input
    document.getElementById("amigo").addEventListener("keypress", (event) => {
        if (event.key === "Enter") {
            agregarAmigo();
        }
    });
});

function agregarAmigo() {
    const inputAmigo = document.getElementById("amigo");
    const nombreAmigo = inputAmigo.value.trim();

    if (!nombreAmigo) {
        alert("Debes ingresar un nombre");
        return;
    }

    if (amigos.includes(nombreAmigo)) {
        alert("Este nombre ya fue agregado.");
        return;
    }

    amigos.push(nombreAmigo);
    inputAmigo.value = "";
    inputAmigo.focus();
    renderizarAmigos();
}

function renderizarAmigos() {
    const listaAmigos = document.getElementById("listaAmigos");
    listaAmigos.innerHTML = amigos.map(amigo => `<li>${amigo}</li>`).join("");
}

function sortearAmigo() {
    if (amigos.length === 0) {
        alert("No hay amigos para sortear");
        return;
    }
    const amigoSorteado = amigos[Math.floor(Math.random() * amigos.length)];
    document.getElementById("resultado").textContent = `El amigo sorteado es: ${amigoSorteado}`;
}
