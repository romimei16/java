# java
code of java
package tugas;

import java.util.Scanner;

public class romi_array {
	int a = 5;
	int[] x = new int[a];
	Scanner sc = new Scanner(System.in);
	
	public void inputdata() {
		for (int i=0;i<a;i++) {
			System.out.print("X["+i+"] = "); x[i]=sc.nextInt();
		}
	}
	
	public void tampilarray() {
		for (int i=0;i<a;i++) {
			System.out.println("X["+i+"]"+"="+x[i]);
		}
	}
	
	public float ratarata() {
		float u, jumlah=0;
		
		for (int i=0;i<a; i++) {
			jumlah=jumlah+x[i];
		}
		u=jumlah/a;
		return u;
	}
	
	int max() {
		int temp=0;
		
		for (int i=0;i<a;i++) {
			if (x[i] > x[temp]) {
				temp = i;
			}
		}
		System.out.println("Index Max : "+temp);
		return temp;
	}
	
	int min() {
		int temp=0;
		
		for (int i=1;i<a;i++) {
			if (x[i] < x[temp]) {
				temp = i;
			}
		}
		System.out.println("Index Min : "+temp);
		return temp;
	}
        
	int SequentialSearch_1() {
		int i, y;
		i=0;
		System.out.println("Y : ");
		y = sc.nextInt();
		
		while ((x[i]!=y)&&(i<a-1)) {
			i=i+1;	
		}
		if (x[i]==y) {
			return i;
		} else {
			return -1;
		}
	}
	
	int SequentialSearch_2() {
		int i, y;
		i=0;
		System.out.println("Y : ");
		y = sc.nextInt();
		
		while ((i<a-1)&&(x[i]!=y)) {
			i=i+1;	
		}
		if (x[i]==y) {
			return i;
		} else {
			return -1;
		}
	}
	
	int SequentialSearch_3() {
		int y;
		int i, idx;
		boolean found = false;
		
		System.out.print("Input Y : "); 
		y = sc.nextInt();
		i=0;
		while ((i<a)&&(!found)) {
			if (x[i]==y) {
				found = true;
			} else {
				i=i+1;
			}
		}
		if (found ==true) {
			return i;
		} else {
			return -1;
		}
	}
	
        public void Binarysearch(){
            int ia=0, ik=a-1, k;
            boolean found=false;
            System.out.print("Input Y : "); 
            int y = sc.nextInt();
            while((ia<=ik)&&(found==false)){
                k =(ia+ik)/2;
                if(x[k]==y){
                    found=true;
                }else if(x[k]<y){
                    ia=k+1;
                }else{
                    ik=k-1;
                }
                if(found==true){
                    System.out.println("ketemu di indeks "+k);
                }else{
                    System.out.println("tidak ketemu");
                }
            }
        }
	
        public void SequentialSearch_Caller() {
		int idx = SequentialSearch_3();
			if (idx!=-1) {
				System.out.println("Telah Ditemukan di Index "+idx);
			} else {
				System.out.println("Tidak Ditemukan");
			}
	}
	
	public void Menu() {
		int input;
		System.out.println("Silahkan Pilih menu dibawah : ");
		System.out.println("1) Nilai Minimal");
                System.out.println("2) Nilai Maximal");
		System.out.println("3) Sequential Search 1");
		System.out.println("4) Sequential Search 2");
		System.out.println("5) Sequential Search 3");
                System.out.println("6) Binary Search");
                System.out.print("masukan :");
		input = sc.nextInt();
		switch (input) {
		case 1:
			min();
		break;
		case 2:
			max();
		break;
		case 3:
			SequentialSearch_1();
		break;
		case 4:
			SequentialSearch_2();
		break;
		case 5:
			SequentialSearch_3();
		break;	
                case 6:
                    for (int i = 0; i < 3; i++) {
                        Binarysearch();
                    }
                break;
		default:
			System.out.println("Menu tidak tersedia");
		break;
		}
	}
	
	public static void main(String[] args) {
		romi_array ra = new romi_array();
		ra.inputdata();
		ra.tampilarray();
		ra.Menu();
	}
}

