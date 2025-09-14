# 1. Flowchart: 
https://drive.google.com/file/d/1AT9BhFSLQq7A07cTW9hKtk1bfYwge6uS/view?usp=sharing

  
# 2. Challenges: 
I think something that was challenging for me was the unintended sharing of variables. When I did a = b, it makes both variables point to the same Box object.
If I wanted independence of these variables, copying both the object and its array before sharing would fix this.
int sum can also overflow with large arrays and values, so instead of using int, I could use long. However, that takes up more storage.

# 3. Video:
https://www.loom.com/share/0f51842703cb49009d2c48d431bf7c76?sid=bed200fd-cb8d-47fe-9b3d-3a18b6e35d53

# 4. Code:
    public class Main {

    static class Box {     //a class that can do something

        int id;          //primitive stored inside the heap object
        int[] data;      //reference to another heap object (array)

        Box(int id, int size) { //2 heap objects overall: box itself and int[] arr
            this.id = id;
            this.data = new int[size];
        }

        int sum() {
            int s = 0;//stack (in this frame)
            for (int v : data) s += v;//local 'v' also on stack
            return s;
        }
    }

    static Box makeBox(int id) { //creates Box size 3; stores id into
                                 // first slot of arr and returns ref to that Box
        Box b = new Box(id, 3);//'b' (ref) on stack → Box object on heap
        b.data[0] = id;
        return b;//returns the reference value
    }
     /*
     below code block: java passes by value; objects mean "by value of the reference."
     temp = local stack var that holds a copy of whatever reference you pass in.
     it still points to the same heap object, so mutations are visible to the caller.
      */
        static void doWork(Box temp) {//'temp' is a stack ref param
            int y = temp.id;//'y' primitive on stack
            temp.data[1] = 99;//mutates heap array via reference
            System.out.println("sum=" + temp.sum());
        }

    public static void main(String[] args) {
        int x = 42;// primitive on stack (main frame)

        Box a = new Box(1, 2);// 'a' (ref) on stack → Box#1 on heap; Box#1 → int[2] on heap
        Box b = makeBox(2);// 'b' (ref) on stack → Box#2 on heap; Box#2 → int[3] on heap
            //after these 2 lines
        
        a = b;//this loses last reference to Box#1, making Box#1 and int[2] arr eligible for garbage collection

        b = null;// 'b' no longer points to Box#2; Box#2 still reachable via 'a', so it is not garbage
        
        doWork(a);// creates a new stack frame; 'temp' points to the same Box#2
            //inside doWork, temp points to same Box#2
            //sets temp.data[1] = 99 then prints sum
            //arr is {2, 99, 0} so sum() returns 101
        
        a = null;// after this line, no references remain to Box#2 → Box#2 and its int[3] eligible for GC
            //no live variables refer to Box #2 or int[3]; both eligible for garbage collection
        
        System.gc(); //"garbage collector, run if you feel like it!"; should trust JVM to do it automatically
    }
    }
`
