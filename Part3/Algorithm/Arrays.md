Arrays 


public class Test{
	public static void main(String[] args){
		int[] a ={3,4,2,1,5,6,4,8,7,8,22,444};

		// sort


		// search


		// Arrays 在 java.utils.arrays 中

		Arrays.sort(a);  // 是使用了快速排序
		for(int x:a){
			System.out.print(x+"");
		}

		float[] f = {1.11f,4.32f,0.999f,908.f};
		Arrays.sort(f);
		for(float x:f){
			System.out.print(x+"  ");
		}

		Arrays.binarySearch(a,4);  // 使用了二分查找
	}
}