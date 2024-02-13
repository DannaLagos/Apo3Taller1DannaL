```
package umariana.taller1;

//Se importo el material necesario para el codigo
import java.util.ArrayList;
import java.util.Scanner;
import mundo.Tarea;


/**
 * @author DANNA LAGOS
 */

public class Taller1 {
    public static void main(String[] args) {

    Scanner lector=new Scanner(System.in);
    boolean activo= true;
    //Me permitira agregar tareas
    boolean tareaAgregada=false;
    //Este Array me permitira guardar informacion
    ArrayList<Tarea> misTareas=new ArrayList<>();

    do{
            //Creamos el menu para que el usuario escoja la opcion 
            System.out.println("===Menu de Opciones==="); 
            System.out.println( "1.Agregar tarea"); 
            System.out.println( "2.Mostrar tarea"); 
            System.out.println( "3.Mostrar Prioridad");
            System.out.println( "4.Teminar programa"); 
            System.out.println( "Seleccione una opcion"); 
     
      // para que el usuario lea la opcion e ingrese la opcion de forma manual  
      int opcion = lector.nextInt();
            //Es una estructura que evalúa más de un caso
            switch(opcion){
                case 1 -> {
                    System.out.println("====AGREGAR TAREA====");
                    System.out.println("Ingrese el id de la tarea");
                    //Permite que el usuario ingrese un numero entero
                    int idTarea = lector.nextInt();
                    //lee una cadena de texto hasta fin de linea
                    lector.nextLine();
                    System.out.println("Ingrese la descripcion de la tarea");
                    //Permite que el usuario ingrese una cadena de caracteres
                    String descripcion = lector.nextLine();
                    //Se define como entero la prioridad 
                    int prioridad;
                    //Do se ejecuta sin evaluar la condicion
                    do {
                        System.out.println("Ingrese la prioridad de la tarea del 1-5");
                        //El usuario interactua al ingresar el valor
                        prioridad = lector.nextInt();
                        //Tiene como condicion ingresar numeros entre el 1 al 5
                        if (prioridad < 1 || prioridad > 5) {
                            System.out.println("La prioridad debe estar entre 1 a 5");
                        }else{   
                            System.out.println("Incorrecto");
                        }
                    } 
                    //El While contiene la condicion
                    while (prioridad < 1 || prioridad > 5);
                    // Se crea el objeto llamado nuevaTarea y se llena la informacion();
                    Tarea nuevaTarea = new Tarea(idTarea, descripcion, prioridad);
                    // Se almacena el objeto en la contenedora
                    misTareas.add(nuevaTarea);
                    System.out.println("Tarea Agregada Correctamente");
                    //Sirve como confirmacion de que la tarea fue agregada
                    tareaAgregada=true;
                }
                case 2 -> {
                    if(tareaAgregada==false){
                        System.out.println("No hay tareas Agregadas");
                    }else{
                        System.out.println("====TAREAS REGISTRADAS CORRECTAMENTE====");
                        //Definimos p como misTareas, y de esta forma llamamos el get que se encuentra en la clase Tarea
                        for(Tarea p: misTareas){
                            //Con el p.get llamamos la informacion que contiene
                            System.out.println("Id: "+p.getIdTarea());
                            System.out.println("Descripcion: "+p.getDescripcion());
                            System.out.println("Prioridad: "+p.getPrioridad());
                            System.out.println("==================");
                        }  
                    }
                }
                case 3 -> { 
                    //Se utiliza la estructura If_Else para ordenar la prioridad  
                    if(tareaAgregada==false){
                        System.out.println("Aun no tienes tareas agregadas");
                    }else{
                        System.out.println("====TAREAS POR ORDEN DE PRIORIDAD====");
                        //con el condicional for organizamos cada una de las tareas desde el mayor hasta el menor
                        for (int i = 5; i >= 1; i--) {
                            for (Tarea p : misTareas) {
                                if (p.getPrioridad() == i) {
                                    System.out.println("Id: " + p.getIdTarea());
                                    System.out.println("Descripción: " + p.getDescripcion());
                                    System.out.println("Prioridad: " + p.getPrioridad());
                               }
                             }
                          }
                        }
                    }
                
                case 4 -> {
                    System.out.println("Has salido del programa, ADIOS");
                    activo=false;
                }
                //
                default -> System.out.println("La opcion que digitalisaste no es valida :( ");
            }
}while(activo);
    
}
        
}
```
