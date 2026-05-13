# Mundial. java

   package Grupo;
   import java.util.*;


    class Grupo { String nombre; Grupo(String n) { nombre = n; } }

    class Equipo {
        private String nombre; 
        private Grupo grupo;
        Equipo(String n, Grupo g) { nombre = n; grupo = g; }
        public String getNombre() { return nombre; }
    }


    abstract class Lamina {
        int numero, cantidad = 1;
        Equipo equipo;
        Lamina(int n, Equipo e) { numero = n; equipo = e; }
    }

    class LaminaJugador extends Lamina {
         private String jugador;
        LaminaJugador(int n, Equipo e, String j) { super(n, e); jugador = j; }
    }

    class LaminaEspecial extends Lamina {
        private String tipo;
        LaminaEspecial(int n, Equipo e, String t) { super(n, e); tipo = t; }
    }


    class Album {
        List<Lamina> coleccion = new ArrayList<>();

        void registrar(Lamina nueva) {
            for (Lamina l : coleccion) {
                if (l.numero == nueva.numero) {
                    l.cantidad++; 
                    return;
                }
            }
            coleccion.add(nueva);
        }

    void mostrarRepetidas() {
        coleccion.stream().filter(l -> l.cantidad > 1)
                 .forEach(l -> System.out.println("Lámina #" + l.numero + " - Repetidas: " + (l.cantidad - 1)));
    }
}
