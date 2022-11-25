# Laboratorio 8 - Librerias #

1. Preparar ambiente <br/>
1.1 Incluir dependencias <br/>
    implementation 'com.airbnb.android:lottie:5.2.0' <br/>
    implementation 'org.quanqi:android-holo-graph:0.1.0' <br/>


2. Crear SplashActivity <br/>
2.1 Crear un Activity llamado SplashActivity <br/>
2.2 Actualizar el archivo activity_splash.xml <br/>
<pre>
<code>
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".SplashActivity">
    <TextView
        android:id="@+id/txtName"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginBottom="20dp"
        android:text="Universidad de Costa Rica"
        android:textColor="@color/purple_200"
        android:textSize="25dp"
        android:textStyle="bold"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintLeft_toLeftOf="parent"
        app:layout_constraintRight_toRightOf="parent" />
    <com.airbnb.lottie.LottieAnimationView
        android:id="@+id/lottieAnimation"
        android:layout_width="400dp"
        android:layout_height="400dp"
        android:elevation="5dp"
        app:layout_constraintBottom_toTopOf="@+id/txtName"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:lottie_autoPlay="true"
        app:lottie_rawRes="@raw/university"/>
</androidx.constraintlayout.widget.ConstraintLayout>
</code>
</pre>


2.3 Actualizar el SplashActivity
<pre>
<code>
public class SplashActivity extends AppCompatActivity {
    TextView appName;
    LottieAnimationView lottieAnimationView;
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_splash);
        appName = findViewById(R.id.txtName);
        lottieAnimationView = findViewById(R.id.lottieAnimation);
        appName.animate().translationY(-400).setDuration(2700).setStartDelay(0);
        lottieAnimationView.animate().translationX(2000).setDuration(2000).setStartDelay(2900);
        new Handler().postDelayed(new Runnable() {
            @Override
            public void run() {
                Intent intent = new Intent(getApplicationContext(), MainActivity.class);
                startActivity(intent);
            }
        }, 5000);
    }
}
</code>
</pre>

2.4 Modificamos el AndroidManifest.xml para que nuestro Activity principal sea el SplashActivity <br/>


3. Crear LottieActivity <br/>
3.1 Crear un Activity llamado LottieActivity <br/>
3.2 Actualizar el archivo activity_lottie.xml <br/>
<pre>
<code>
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="@android:color/white"
    tools:context=".LottieActivity">
    <com.airbnb.lottie.LottieAnimationView
        android:id="@+id/lav_actionBar"
        android:layout_width="match_parent"
        android:layout_height="75dp"
        android:layout_marginStart="0dp"
        android:layout_marginTop="0dp"
        android:layout_marginEnd="0dp"
        android:scaleType="centerCrop"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:lottie_autoPlay="true"
        app:lottie_fileName="gradient_bg.json"
        app:lottie_loop="true" />
    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="8dp"
        android:layout_marginTop="8dp"
        android:layout_marginEnd="8dp"
        android:text="@string/app_holo_graph"
        android:textColor="@android:color/white"
        android:textSize="30sp"
        app:layout_constraintBottom_toBottomOf="@+id/lav_actionBar"
        app:layout_constraintEnd_toEndOf="@+id/lav_actionBar"
        app:layout_constraintHorizontal_bias="0.0"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="@+id/lav_actionBar" />
    <com.airbnb.lottie.LottieAnimationView
        android:id="@+id/lav_thumbUp"
        android:layout_width="100dp"
        android:layout_height="100dp"
        android:layout_marginStart="80dp"
        android:layout_marginTop="8dp"
        android:layout_marginBottom="8dp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:lottie_autoPlay="false"
        app:lottie_fileName="thumb_up.json"
        app:lottie_loop="false"
        app:lottie_speed="1.25" />
    <com.airbnb.lottie.LottieAnimationView
        android:id="@+id/lav_thumbDown"
        android:layout_width="100dp"
        android:layout_height="100dp"
        android:layout_marginTop="8dp"
        android:layout_marginEnd="80dp"
        android:layout_marginBottom="8dp"
        android:rotation="180"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:lottie_autoPlay="false"
        app:lottie_fileName="thumb_up.json"
        app:lottie_loop="false"
        app:lottie_speed="1.25" />
    <com.airbnb.lottie.LottieAnimationView
        android:id="@+id/lav_toggle"
        android:layout_width="wrap_content"
        android:layout_height="100dp"
        android:layout_marginStart="8dp"
        android:layout_marginTop="8dp"
        android:layout_marginEnd="8dp"
        android:layout_marginBottom="8dp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/lav_thumbUp"
        app:layout_constraintVertical_bias="0.4"
        app:lottie_autoPlay="false"
        app:lottie_fileName="toggle_switch.json"
        app:lottie_loop="false"
        app:lottie_speed="1.75" />
</androidx.constraintlayout.widget.ConstraintLayout>
</code>
</pre>

3.3 Actualizar el LottieActivity
<pre>
<code>
public class LottieActivity extends AppCompatActivity {
    LottieAnimationView thumb_up;
    LottieAnimationView thumb_down;
    LottieAnimationView toggle;
    int flag = 0;
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_lottie);
        thumb_up = findViewById(R.id.lav_thumbUp);
        thumb_up.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                thumb_down.setProgress(0);
                thumb_down.pauseAnimation();
                thumb_up.playAnimation();
            }
        });
        thumb_down = findViewById(R.id.lav_thumbDown);
        thumb_down.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                thumb_up.setProgress(0);
                thumb_up.pauseAnimation();
                thumb_down.playAnimation();
            }
        });
        toggle = findViewById(R.id.lav_toggle);
        toggle.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                changeState();
            }
        });
    }
    private void changeState() {
        if (flag == 0) {
            toggle.setMinAndMaxProgress(0f, 0.43f); 
            toggle.playAnimation();
            flag = 1;
        } else {
            toggle.setMinAndMaxProgress(0.5f, 1f);
            toggle.playAnimation();
            flag = 0;
        }
    }
}
</code>
</pre>
3.4 Modificamos el MainActivity <br/>
<pre>
<code>
    //Invoca el activity de Lottie
    public void activityLottie(View view)
    {
        Intent intent = new Intent(getApplicationContext(), LottieActivity.class);
        startActivity(intent);
    }
</code>
</pre>
3.5 Modificamos el activity_main.xml <br/>
<pre>
<code>
<?xml version="1.0" encoding="utf-8"?>
<ScrollView xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">
    <androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
        xmlns:app="http://schemas.android.com/apk/res-auto"
        xmlns:tools="http://schemas.android.com/tools"
        android:layout_width="match_parent"
        android:layout_height="match_parent">
        <Button
            android:id="@+id/btnLottie"
            android:layout_width="0dp"
            android:layout_height="wrap_content"
            android:layout_marginEnd="40dp"
            android:layout_marginStart="40dp"
            android:layout_marginTop="16dp"
            android:text="@string/btnLottie"
            android:onClick="activityLottie"
            app:layout_constraintLeft_toLeftOf="parent"
            app:layout_constraintRight_toRightOf="parent"
            app:layout_constraintTop_toTopOf="parent"
            tools:layout_constraintLeft_creator="1"
            tools:layout_constraintRight_creator="1"/>
    </androidx.constraintlayout.widget.ConstraintLayout>
</ScrollView>
</code>
</pre>

4. Crear HoloGraphActivity <br/>
4.1 Crear un Activity llamado HoloGraphActivity <br/>
4.2 Actualizar el archivo activity_holo_graph.xml <br/>
<pre>
<code>
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".ShimmerActivity">
    <com.echo.holographlibrary.BarGraph
        android:layout_width="match_parent"
        android:layout_height="200dp"
        android:id="@+id/graph"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent" />
    <com.echo.holographlibrary.PieGraph
        android:layout_width="match_parent"
        android:layout_height="200dp"
        android:id="@+id/graph1"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"/>
</androidx.constraintlayout.widget.ConstraintLayout>
</code>
</pre>

4.3 Actualizar el HoloGraphActivity
<pre>
<code>
        ArrayList<Bar> points = new ArrayList<Bar>();
        Bar d = new Bar();
        d.setColor(Color.parseColor("#0B6623"));
        d.setName("Test1");
        d.setValue(10);
        Bar d2 = new Bar();
        d2.setColor(Color.parseColor("#7C0A02"));
        d2.setName("Test2");
        d2.setValue(20);
        points.add(d);
        points.add(d2);

        BarGraph g = (BarGraph)findViewById(R.id.graph);
        g.setBars(points);

        PieGraph pg = (PieGraph)findViewById(R.id.graph1);
        PieSlice slice = new PieSlice();
        slice.setColor(Color.parseColor("#004F98"));
        slice.setValue(2);
        pg.addSlice(slice);
        slice = new PieSlice();
        slice.setColor(Color.parseColor("#0B6623"));
        slice.setValue(3);
        pg.addSlice(slice);
        slice = new PieSlice();
        slice.setColor(Color.parseColor("#7C0A02"));
        slice.setValue(8);
        pg.addSlice(slice);
</code>
</pre>
4.4 Modificamos el MainActivity <br/>
<pre>
<code>
    public void activityHoloGraph(View view)
    {
        Intent intent = new Intent(getApplicationContext(), HoloGraphActivity.class);
        startActivity(intent);
    }
</code>
</pre>
4.5 Modificamos el activity_main.xml <br/>
<pre>
<code>
        <Button
            android:id="@+id/btnHoloGraph"
            android:layout_width="0dp"
            android:layout_height="wrap_content"
            android:layout_marginEnd="40dp"
            android:layout_marginStart="40dp"
            android:layout_marginTop="16dp"
            android:text="@string/btnHoloGraph"
            android:onClick="activityHoloGraph"
            app:layout_constraintLeft_toLeftOf="parent"
            app:layout_constraintRight_toRightOf="parent"
            app:layout_constraintTop_toBottomOf="@+id/btnLottie"
            tools:layout_constraintLeft_creator="1"
            tools:layout_constraintRight_creator="1"/>
</code>
</pre>

# Laboratorio 8 - Librerias - Parte II #

5. Crear ShimmerActivity <br/>
5.1 Crear un Activity llamado ShimmerActivity <br/>
5.2 Actualizar el archivo activity_shimmer.xml <br/>
5.3 Incluir las siguientes referencias <br/>
    implementation 'com.squareup.picasso:picasso:2.8' <br/>
    implementation 'com.android.volley:volley:1.2.1' <br/>
    implementation 'com.facebook.shimmer:shimmer:0.5.0'  <br/>
5.4 Agregar el permiso android.permission.INTERNET<br/>
5.5 Creamos las carpetas Adapter y Model<br/>
5.6 Creamos las clases Model->Products y Adapter->RecyclerViewAdapter <br/>
5.7 Cremos 2 view nuevos<br/>
res->layout->item_product_list.xml <br/>
res->layout->shimmer_placeholder_layout.xml  <br/>
5.8 Actualizamos el item_product_list.xml 
<pre>
<code>
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    tools:ignore="HardcodedText,MissingConstraints"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:padding="20dp">

    <ImageView
        android:id="@+id/item_profile_img"
        android:layout_width="100dp"
        android:layout_height="100dp"
        android:src="@drawable/ic_launcher_background"
        app:layout_constraintTop_toTopOf="parent"
        tools:ignore="ContentDescription,MissingConstraints" />

    <TextView
        android:id="@+id/item_product_name_title"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="15dp"
        android:text="Product name"
        android:textStyle="bold"
        app:layout_constraintStart_toEndOf="@+id/item_profile_img" />

    <TextView
        android:id="@+id/item_product_price"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="15dp"
        android:layout_marginTop="8dp"
        android:text="Product Price"
        app:layout_constraintStart_toEndOf="@+id/item_profile_img"
        app:layout_constraintTop_toBottomOf="@+id/item_product_name_title" />

    <TextView
        android:id="@+id/item_product_rating"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="15dp"
        android:layout_marginTop="8dp"
        android:text="Product Rating"
        app:layout_constraintStart_toEndOf="@+id/item_profile_img"
        app:layout_constraintTop_toBottomOf="@+id/item_product_price" />

    <TextView
        android:id="@+id/item_product_description"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="15dp"
        android:layout_marginTop="8dp"
        android:text="Product description"
        app:layout_constraintTop_toBottomOf="@+id/item_profile_img"
        tools:ignore="MissingConstraints" />

    <View
        android:id="@+id/name"
        android:layout_width="match_parent"
        android:layout_height="3dp"
        android:background="@color/shimmer_placeholder"
        android:layout_marginTop="3dp"
        app:layout_constraintTop_toBottomOf="@+id/item_product_description"/>

</androidx.constraintlayout.widget.ConstraintLayout>
</code>
</pre>
5.9 En el archivo de colores incluimos el siguiente: <br/>
    <color name="shimmer_placeholder">#dddddd</color><br/>
5.10 Actualizamos el archivo shimmer_placeholder_layout.xml 
<pre>
<code>
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    tools:ignore="HardcodedText,MissingConstraints"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:padding="20dp">

    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:id="@+id/layout"
        android:padding="3dp"
        android:orientation="horizontal">

        <ImageView
            android:id="@+id/item_profile_img"
            android:layout_width="100dp"
            android:layout_height="100dp"
            android:layout_marginBottom="25dp"
            android:background="@color/shimmer_placeholder"
            app:layout_constraintTop_toTopOf="parent"
            tools:ignore="ContentDescription,MissingConstraints" />

        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:layout_marginBottom="40dp"
            android:layout_marginTop="20dp"
            android:orientation="vertical">
            <TextView
                android:id="@+id/item_product_name_title"
                android:layout_width="150dp"
                android:layout_height="15dp"
                android:layout_marginStart="15dp"
                android:background="@color/shimmer_placeholder"
                app:layout_constraintStart_toEndOf="@+id/item_profile_img" />

            <TextView
                android:id="@+id/item_product_price"
                android:layout_width="200dp"
                android:layout_height="15dp"
                android:layout_marginStart="15dp"
                android:layout_marginTop="8dp"
                android:background="@color/shimmer_placeholder"
                app:layout_constraintStart_toEndOf="@+id/item_profile_img"
                app:layout_constraintTop_toBottomOf="@+id/item_product_name_title" />

            <TextView
                android:id="@+id/item_product_rating"
                android:layout_width="250dp"
                android:layout_height="15dp"
                android:layout_marginStart="15dp"
                android:layout_marginTop="8dp"
                android:background="@color/shimmer_placeholder"
                app:layout_constraintStart_toEndOf="@+id/item_profile_img"
                app:layout_constraintTop_toBottomOf="@+id/item_product_college" />
        </LinearLayout>
    </LinearLayout>

    <TextView
        android:id="@+id/item_product_description"
        android:layout_width="385dp"
        android:layout_height="20dp"
        android:layout_marginStart="3dp"
        android:layout_alignBottom="@id/layout"
        android:background="@color/shimmer_placeholder"
        tools:ignore="MissingConstraints" />
</RelativeLayout>
</pre>
</code>

5.10 Actualizamos el archivo activity_shimmer.xml 
<pre>
<code>
<?xml version="1.0" encoding="utf-8"?>
<androidx.coordinatorlayout.widget.CoordinatorLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".ShimmerActivity">
    <com.facebook.shimmer.ShimmerFrameLayout
        android:id="@+id/shimmerLayout"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        tools:ignore="MissingConstraints">
        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:orientation="vertical">
            <include layout="@layout/shimmer_placeholder_layout"></include>

            <include layout="@layout/shimmer_placeholder_layout"></include>

            <include layout="@layout/shimmer_placeholder_layout"></include>

            <include layout="@layout/shimmer_placeholder_layout"></include>

            <include layout="@layout/shimmer_placeholder_layout"></include>

            <include layout="@layout/shimmer_placeholder_layout"></include>

            <include layout="@layout/shimmer_placeholder_layout"></include>
        </LinearLayout>
    </com.facebook.shimmer.ShimmerFrameLayout>
    <androidx.recyclerview.widget.RecyclerView
        android:layout_width="wrap_content"
        android:layout_height="match_parent"
        android:layout_marginStart="3dp"
        android:layout_marginEnd="3dp"
        android:layout_marginTop="3dp"
        android:id="@+id/RV_product_list"
        android:visibility="gone"
        tools:listitem="@layout/item_product_list"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"/>
</androidx.coordinatorlayout.widget.CoordinatorLayout>
</pre>
</code>

5.11 Actualizamos el archivo Products 
<pre>
<code>

public class Products {
    private long id;
    private String title;
    private String description;
    private long price;
    private double discountPercentage;
    private double rating;
    private long stock;
    private String brand;
    private String category;
    private String thumbnail;
    private String[] images;

    public long getID() { return id; }
    public void setID(long value) { this.id = value; }

    public String getTitle() { return title; }
    public void setTitle(String value) { this.title = value; }

    public String getDescription() { return description; }
    public void setDescription(String value) { this.description = value; }

    public long getPrice() { return price; }
    public void setPrice(long value) { this.price = value; }

    public double getDiscountPercentage() { return discountPercentage; }
    public void setDiscountPercentage(double value) { this.discountPercentage = value; }

    public double getRating() { return rating; }
    public void setRating(double value) { this.rating = value; }

    public long getStock() { return stock; }
    public void setStock(long value) { this.stock = value; }

    public String getBrand() { return brand; }
    public void setBrand(String value) { this.brand = value; }

    public String getCategory() { return category; }
    public void setCategory(String value) { this.category = value; }

    public String getThumbnail() { return thumbnail; }
    public void setThumbnail(String value) { this.thumbnail = value; }

    public String[] getImages() { return images; }
    public void setImages(String[] value) { this.images = value; }
}

</pre>
</code>

5.12 Actualizamos el archivo RecyclerViewAdapter
<pre>
<code>

public class RecyclerViewAdapter extends RecyclerView.Adapter<RecyclerViewAdapter.MyViewHolder>{

    private Context mContext ;
    private List<Products> mData ;

    public RecyclerViewAdapter(Context mContext, List<Products> mData) {
        this.mContext = mContext;
        this.mData = mData;
    }

    @NonNull
    @Override
    public MyViewHolder onCreateViewHolder(@NonNull ViewGroup parent, int viewType) {
        View view ;
        LayoutInflater inflater = LayoutInflater.from(mContext);
        view = inflater.inflate(R.layout.item_product_list,parent,false) ;
        return new MyViewHolder(view) ;
    }

    static class MyViewHolder extends RecyclerView.ViewHolder {
        TextView tv_product_name;
        TextView tv_product_price;
        TextView tv_product_rating;
        TextView tv_product_description;
        ImageView img_product_profile;

        MyViewHolder(View itemView) {
            super(itemView);
            tv_product_name = itemView.findViewById(R.id.item_product_name_title);
            tv_product_price = itemView.findViewById(R.id.item_product_price);
            tv_product_rating = itemView.findViewById(R.id.item_product_rating);
            tv_product_description = itemView.findViewById(R.id.item_product_description);
            img_product_profile = itemView.findViewById(R.id.item_profile_img);
        }
    }

    @Override
    public int getItemCount() {
        return mData.size();
    }

    @Override
    public void onBindViewHolder(@NonNull MyViewHolder holder, int position) {
        holder.tv_product_name.setText(mData.get(position).getTitle());
        holder.tv_product_price.setText("$"+mData.get(position).getPrice());
        holder.tv_product_rating.setText("Rating:"+mData.get(position).getRating());
        holder.tv_product_description.setText(mData.get(position).getDescription());
        Picasso.get()
                .load(mData.get(position).getThumbnail())
                .into(holder.img_product_profile);
    }
}

</code>
</pre>

5.13 Actualizamos el archivo ShimmerActivity
<pre>
<code>
public class ShimmerActivity extends AppCompatActivity {
    private JsonObjectRequest mJsonObjectRequest;
    private RequestQueue mRequestQueue;
    private List<Products> productsList = new ArrayList<>();
    private RecyclerView mRecyclerView;
    private ShimmerFrameLayout mFrameLayout;
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_shimmer);
        mRecyclerView = findViewById(R.id.RV_product_list);
        mFrameLayout = findViewById(R.id.shimmerLayout);
        RequestJsonData();
    }
    public void RequestJsonData() {
        mJsonObjectRequest = new JsonObjectRequest(Request.Method.GET,
                "https://dummyjson.com/products",
                null,
                new Response.Listener<JSONObject>() {
                    @Override
                    public void onResponse(JSONObject response) {
                        try {
                            JSONArray array =  response.getJSONArray("products");
                            for (int i = 0; i < array.length(); i++) {
                                JSONObject jsonObject = array.getJSONObject(i);
                                Products product = new Products();
                                product.setTitle(jsonObject.getString("title"));
                                product.setPrice(jsonObject.getLong("price"));
                                product.setRating(jsonObject.getLong("rating"));
                                product.setDescription(jsonObject.getString("description"));
                                product.setThumbnail(jsonObject.getString("thumbnail"));
                                productsList.add(product);
                            }
                        } catch (JSONException e) {
                            e.printStackTrace();
                        }
                        SetRecyclerViewAdapter(productsList);
                        mFrameLayout.startShimmer();
                        mFrameLayout.setVisibility(View.GONE);
                        mRecyclerView.setVisibility(View.VISIBLE);
                    }
                },
                new Response.ErrorListener() {
                    @Override
                    public void onErrorResponse(VolleyError error) {

                    }
                });

        mRequestQueue = Volley.newRequestQueue(ShimmerActivity.this);
        mRequestQueue.add(mJsonObjectRequest);
    }
    public void SetRecyclerViewAdapter(List<Products> list) {
        RecyclerViewAdapter myAdapter = new RecyclerViewAdapter(this, list);
        mRecyclerView.setLayoutManager(new LinearLayoutManager(this));
        mRecyclerView.setAdapter(myAdapter);
    }
    @Override
    protected void onResume() {
        mFrameLayout.startShimmer();
        super.onResume();
    }
    @Override
    protected void onPause() {
        mFrameLayout.stopShimmer();
        super.onPause();
    }
}
</code>
</pre>

5.14 Actualizamos el archivo activity_main.xml
<pre>
<code>
        <Button
            android:id="@+id/btnShimmer"
            android:layout_width="0dp"
            android:layout_height="wrap_content"
            android:layout_marginEnd="40dp"
            android:layout_marginStart="40dp"
            android:layout_marginTop="16dp"
            android:text="@string/btnShimmer"
            android:onClick="activityShimmer"
            app:layout_constraintLeft_toLeftOf="parent"
            app:layout_constraintRight_toRightOf="parent"
            app:layout_constraintTop_toBottomOf="@+id/btnHoloGraph"
            tools:layout_constraintLeft_creator="1"
            tools:layout_constraintRight_creator="1"/>
</code>
</pre>
5.15 Incluimos el siguiente evento en el MainActivity
<pre>
<code>
    public void activityShimmer(View view)
    {
        Intent intent = new Intent(getApplicationContext(), ShimmerActivity.class);
        startActivity(intent);
    }
</code>
</pre>

6. Crear GameActivity <br/>
6.1 Crear un Activity llamado GameActivity <br/>
6.2 Colocar el atributo android:screenOrientation="landscape" al activity <br/>
6.3 Descargar el archivo Recursos Lab 8.zip de mediación y colocar los archivos en las siguientes rutas: <br/>
    chibi1.png -> drawable <br/>
    chibi2.png -> drawable <br/>
    explosion.png -> drawable <br/>
    background.mp3 -> raw <br/>
    explosion.wav -> raw <br/>
6.4 Incluir el siguiente atributo al archivo de strings.xml <br/>
  <string name="btnGame">Game</string> <br/>
6.5 Crear la carpeta Game y las siguientes clases:<br/>
    ChibiCharacter <br/>
    Explosion<br/>
    GameObject (abstract)<br/>
    GameSurface<br/>
    GameThread<br/>
6.6 Actualizamos el contenido de la clase ChibiCharacter
<pre>
<code>
public  class ChibiCharacter extends GameObject  {

    private static final int ROW_TOP_TO_BOTTOM = 0;
    private static final int ROW_RIGHT_TO_LEFT = 1;
    private static final int ROW_LEFT_TO_RIGHT = 2;
    private static final int ROW_BOTTOM_TO_TOP = 3;

    // Row index of Image are being used.
    private int rowUsing = ROW_LEFT_TO_RIGHT;

    private int colUsing;

    private Bitmap[] leftToRights;
    private Bitmap[] rightToLefts;
    private Bitmap[] topToBottoms;
    private Bitmap[] bottomToTops;

    // Velocity of game character (pixel/millisecond)
    public static final float VELOCITY = 0.1f;

    private int movingVectorX = 10;
    private int movingVectorY = 5;

    private long lastDrawNanoTime =-1;

    private GameSurface gameSurface;

    public ChibiCharacter(GameSurface gameSurface, Bitmap image, int x, int y) {
        super(image, 4, 3, x, y);

        this.gameSurface= gameSurface;

        this.topToBottoms = new Bitmap[colCount]; // 3
        this.rightToLefts = new Bitmap[colCount]; // 3
        this.leftToRights = new Bitmap[colCount]; // 3
        this.bottomToTops = new Bitmap[colCount]; // 3

        for(int col = 0; col< this.colCount; col++ ) {
            this.topToBottoms[col] = this.createSubImageAt(ROW_TOP_TO_BOTTOM, col);
            this.rightToLefts[col]  = this.createSubImageAt(ROW_RIGHT_TO_LEFT, col);
            this.leftToRights[col] = this.createSubImageAt(ROW_LEFT_TO_RIGHT, col);
            this.bottomToTops[col]  = this.createSubImageAt(ROW_BOTTOM_TO_TOP, col);
        }
    }

    public Bitmap[] getMoveBitmaps()  {
        switch (rowUsing)  {
            case ROW_BOTTOM_TO_TOP:
                return  this.bottomToTops;
            case ROW_LEFT_TO_RIGHT:
                return this.leftToRights;
            case ROW_RIGHT_TO_LEFT:
                return this.rightToLefts;
            case ROW_TOP_TO_BOTTOM:
                return this.topToBottoms;
            default:
                return null;
        }
    }

    public Bitmap getCurrentMoveBitmap()  {
        Bitmap[] bitmaps = this.getMoveBitmaps();
        return bitmaps[this.colUsing];
    }


    public void update()  {
        this.colUsing++;
        if(colUsing >= this.colCount)  {
            this.colUsing =0;
        }
        // Current time in nanoseconds
        long now = System.nanoTime();

        // Never once did draw.
        if(lastDrawNanoTime==-1) {
            lastDrawNanoTime= now;
        }
        // Change nanoseconds to milliseconds (1 nanosecond = 1000000 milliseconds).
        int deltaTime = (int) ((now - lastDrawNanoTime)/ 1000000 );

        // Distance moves
        float distance = VELOCITY * deltaTime;

        double movingVectorLength = Math.sqrt(movingVectorX* movingVectorX + movingVectorY*movingVectorY);

        // Calculate the new position of the game character.
        this.x = x +  (int)(distance* movingVectorX / movingVectorLength);
        this.y = y +  (int)(distance* movingVectorY / movingVectorLength);

        // When the game's character touches the edge of the screen, then change direction

        if(this.x < 0 )  {
            this.x = 0;
            this.movingVectorX = - this.movingVectorX;
        } else if(this.x > this.gameSurface.getWidth() -width)  {
            this.x= this.gameSurface.getWidth()-width;
            this.movingVectorX = - this.movingVectorX;
        }

        if(this.y < 0 )  {
            this.y = 0;
            this.movingVectorY = - this.movingVectorY;
        } else if(this.y > this.gameSurface.getHeight()- height)  {
            this.y= this.gameSurface.getHeight()- height;
            this.movingVectorY = - this.movingVectorY ;
        }

        // rowUsing
        if( movingVectorX > 0 )  {
            if(movingVectorY > 0 && Math.abs(movingVectorX) < Math.abs(movingVectorY)) {
                this.rowUsing = ROW_TOP_TO_BOTTOM;
            }else if(movingVectorY < 0 && Math.abs(movingVectorX) < Math.abs(movingVectorY)) {
                this.rowUsing = ROW_BOTTOM_TO_TOP;
            }else  {
                this.rowUsing = ROW_LEFT_TO_RIGHT;
            }
        } else {
            if(movingVectorY > 0 && Math.abs(movingVectorX) < Math.abs(movingVectorY)) {
                this.rowUsing = ROW_TOP_TO_BOTTOM;
            }else if(movingVectorY < 0 && Math.abs(movingVectorX) < Math.abs(movingVectorY)) {
                this.rowUsing = ROW_BOTTOM_TO_TOP;
            }else  {
                this.rowUsing = ROW_RIGHT_TO_LEFT;
            }
        }
    }

    public void draw(Canvas canvas)  {
        Bitmap bitmap = this.getCurrentMoveBitmap();
        canvas.drawBitmap(bitmap,x, y, null);
        // Last draw time.
        this.lastDrawNanoTime= System.nanoTime();
    }

    public void setMovingVector(int movingVectorX, int movingVectorY)  {
        this.movingVectorX= movingVectorX;
        this.movingVectorY = movingVectorY;
    }
}
</code>
</pre>


6.7 Actualizamos el contenido de la clase Explosion
<pre>
<code>
public class Explosion extends GameObject{
    private int rowIndex = 0 ;
    private int colIndex = -1 ;

    private boolean finish= false;
    private GameSurface gameSurface;

    public Explosion(GameSurface GameSurface, Bitmap image, int x, int y) {
        super(image, 5, 5, x, y);

        this.gameSurface= GameSurface;
    }

    public void update()  {
        this.colIndex++;

        // Play sound explosion.wav.
        if(this.colIndex==0 && this.rowIndex==0) {
            this.gameSurface.playSoundExplosion();
        }

        if(this.colIndex >= this.colCount)  {
            this.colIndex =0;
            this.rowIndex++;

            if(this.rowIndex>= this.rowCount)  {
                this.finish= true;
            }
        }
    }

    public void draw(Canvas canvas)  {
        if(!finish)  {
            Bitmap bitmap= this.createSubImageAt(rowIndex,colIndex);
            canvas.drawBitmap(bitmap, this.x, this.y,null);
        }
    }

    public boolean isFinish() {
        return finish;
    }
}
</code>
</pre>

6.7 Actualizamos el contenido de la clase GameObject 
<pre>
<code>
public abstract class GameObject {
    protected Bitmap image;

    protected final int rowCount;
    protected final int colCount;

    protected final int WIDTH;
    protected final int HEIGHT;

    protected final int width;


    protected final int height;
    protected int x;
    protected int y;

    public GameObject(Bitmap image, int rowCount, int colCount, int x, int y) {

        this.image = image;
        this.rowCount = rowCount;
        this.colCount = colCount;

        this.x = x;
        this.y = y;

        this.WIDTH = image.getWidth();
        this.HEIGHT = image.getHeight();

        this.width = this.WIDTH / colCount;
        this.height = this.HEIGHT / rowCount;
    }


    protected Bitmap createSubImageAt(int row, int col) {
        // createBitmap(bitmap, x, y, width, height).
        Bitmap subImage = Bitmap.createBitmap(image, col * width, row * height, width, height);
        return subImage;
    }

    public int getX() {
        return this.x;
    }

    public int getY() {
        return this.y;
    }


    public int getHeight() {
        return height;
    }

    public int getWidth() {
        return width;
    }
}
</code>
</pre>
6.8 Actualizamos el contenido de la clase GameSurface 
<pre>
<code>
public class GameSurface extends SurfaceView implements SurfaceHolder.Callback {
    private GameThread gameThread;

    private final List<ChibiCharacter> chibiList = new ArrayList<ChibiCharacter>();
    private final List<Explosion> explosionList = new ArrayList<Explosion>();

    private static final int MAX_STREAMS=100;
    private int soundIdExplosion;
    private int soundIdBackground;

    private boolean soundPoolLoaded;
    private SoundPool soundPool;


    public GameSurface(Context context)  {
        super(context);

        // Make Game Surface focusable so it can handle events.
        this.setFocusable(true);

        // Sét callback.
        this.getHolder().addCallback(this);

        this.initSoundPool();
    }

    private void initSoundPool()  {
        // With Android API >= 21.
        if (Build.VERSION.SDK_INT >= 21 ) {

            AudioAttributes audioAttrib = new AudioAttributes.Builder()
                    .setUsage(AudioAttributes.USAGE_GAME)
                    .setContentType(AudioAttributes.CONTENT_TYPE_SONIFICATION)
                    .build();

            SoundPool.Builder builder= new SoundPool.Builder();
            builder.setAudioAttributes(audioAttrib).setMaxStreams(MAX_STREAMS);

            this.soundPool = builder.build();
        }
        // With Android API < 21
        else {
            // SoundPool(int maxStreams, int streamType, int srcQuality)
            this.soundPool = new SoundPool(MAX_STREAMS, AudioManager.STREAM_MUSIC, 0);
        }

        // When SoundPool load complete.
        this.soundPool.setOnLoadCompleteListener(new SoundPool.OnLoadCompleteListener() {
            @Override
            public void onLoadComplete(SoundPool soundPool, int sampleId, int status) {
                soundPoolLoaded = true;

                // Playing background sound.
                playSoundBackground();
            }
        });

        // Load the sound background.mp3 into SoundPool
        this.soundIdBackground= this.soundPool.load(this.getContext(), R.raw.background,1);

        // Load the sound explosion.wav into SoundPool
        this.soundIdExplosion = this.soundPool.load(this.getContext(), R.raw.explosion,1);


    }

    public void playSoundExplosion()  {
        if(this.soundPoolLoaded) {
            float leftVolumn = 0.8f;
            float rightVolumn =  0.8f;
            // Play sound explosion.wav
            int streamId = this.soundPool.play(this.soundIdExplosion,leftVolumn, rightVolumn, 1, 0, 1f);
        }
    }

    public void playSoundBackground()  {
        if(this.soundPoolLoaded) {
            float leftVolumn = 0.8f;
            float rightVolumn =  0.8f;
            // Play sound background.mp3
            int streamId = this.soundPool.play(this.soundIdBackground,leftVolumn, rightVolumn, 1, -1, 1f);
        }
    }

    @Override
    public boolean onTouchEvent(MotionEvent event) {
        if (event.getAction() == MotionEvent.ACTION_DOWN) {

            int x=  (int)event.getX();
            int y = (int)event.getY();

            Iterator<ChibiCharacter> iterator= this.chibiList.iterator();


            while(iterator.hasNext()) {
                ChibiCharacter chibi = iterator.next();
                if( chibi.getX() < x && x < chibi.getX() + chibi.getWidth()
                        && chibi.getY() < y && y < chibi.getY()+ chibi.getHeight())  {
                    // Remove the current element from the iterator and the list.
                    iterator.remove();

                    // Create Explosion object.
                    Bitmap bitmap = BitmapFactory.decodeResource(this.getResources(),R.drawable.explosion);
                    Explosion explosion = new Explosion(this, bitmap,chibi.getX(),chibi.getY());

                    this.explosionList.add(explosion);
                }
            }


            for(ChibiCharacter chibi: chibiList) {
                int movingVectorX =x-  chibi.getX() ;
                int movingVectorY =y-  chibi.getY() ;
                chibi.setMovingVector(movingVectorX, movingVectorY);
            }
            return true;
        }
        return false;
    }

    public void update()  {
        for(ChibiCharacter chibi: chibiList) {
            chibi.update();
        }
        for(Explosion explosion: this.explosionList)  {
            explosion.update();
        }

        Iterator<Explosion> iterator= this.explosionList.iterator();
        while(iterator.hasNext())  {
            Explosion explosion = iterator.next();

            if(explosion.isFinish()) {
                // If explosion finish, Remove the current element from the iterator & list.
                iterator.remove();
                continue;
            }
        }
    }

    @Override
    public void draw(Canvas canvas)  {
        super.draw(canvas);

        for(ChibiCharacter chibi: chibiList)  {
            chibi.draw(canvas);
        }

        for(Explosion explosion: this.explosionList)  {
            explosion.draw(canvas);
        }

    }

    // Implements method of SurfaceHolder.Callback
    @Override
    public void surfaceCreated(SurfaceHolder holder) {
        Bitmap chibiBitmap1 = BitmapFactory.decodeResource(this.getResources(),R.drawable.chibi1);
        ChibiCharacter chibi1 = new ChibiCharacter(this,chibiBitmap1,100,50);

        Bitmap chibiBitmap2 = BitmapFactory.decodeResource(this.getResources(),R.drawable.chibi2);
        ChibiCharacter chibi2 = new ChibiCharacter(this,chibiBitmap2,300,150);

        this.chibiList.add(chibi1);
        this.chibiList.add(chibi2);

        this.gameThread = new GameThread(this,holder);
        this.gameThread.setRunning(true);
        this.gameThread.start();
    }

    // Implements method of SurfaceHolder.Callback
    @Override
    public void surfaceChanged(SurfaceHolder holder, int format, int width, int height) {

    }

    // Implements method of SurfaceHolder.Callback
    @Override
    public void surfaceDestroyed(SurfaceHolder holder) {
        boolean retry= true;
        while(retry) {
            try {
                this.gameThread.setRunning(false);

                // Parent thread must wait until the end of GameThread.
                this.gameThread.join();
            }catch(InterruptedException e)  {
                e.printStackTrace();
            }
            retry= true;
        }
    }
}
</code>
</pre>

6.9 Actualizamos el contenido de la clase GameSurface 
<pre>
<code>
public class GameThread extends Thread {
    private boolean running;
    private GameSurface gameSurface;
    private SurfaceHolder surfaceHolder;

    public GameThread(GameSurface gameSurface, SurfaceHolder surfaceHolder)  {
        this.gameSurface= gameSurface;
        this.surfaceHolder= surfaceHolder;
    }

    @Override
    public void run()  {
        long startTime = System.nanoTime();

        while(running)  {
            Canvas canvas= null;
            try {
                // Get Canvas from Holder and lock it.
                canvas = this.surfaceHolder.lockCanvas();

                // Synchronized
                synchronized (canvas)  {
                    this.gameSurface.update();
                    this.gameSurface.draw(canvas);
                }
            }catch(Exception e)  {
                // Do nothing.
            } finally {
                if(canvas!= null)  {
                    // Unlock Canvas.
                    this.surfaceHolder.unlockCanvasAndPost(canvas);
                }
            }
            long now = System.nanoTime() ;
            // Interval to redraw game
            // (Change nanoseconds to milliseconds)
            long waitTime = (now - startTime)/1000000;
            if(waitTime < 10)  {
                waitTime= 10; // Millisecond.
            }
            System.out.print(" Wait Time="+ waitTime);

            try {
                // Sleep.
                this.sleep(waitTime);
            } catch(InterruptedException e)  {

            }
            startTime = System.nanoTime();
            System.out.print(".");
        }
    }

    public void setRunning(boolean running)  {
        this.running= running;
    }
}
</code>
</pre>

6.10 Actualizamos el contenido de la clase GameActivity
<pre>
<code>
public class GameActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_game);
        //FullScreen
        this.getWindow().setFlags(WindowManager.LayoutParams.FLAG_FULLSCREEN, WindowManager.LayoutParams.FLAG_FULLSCREEN);

        this.setContentView(new GameSurface(this));
    }
}
</code>
</pre>

6.11 En la clase activity_game.xml debe dejar únicamente ConstraintLayout 
6.12 Incluir el botón en el activity_main.xml 
<pre>
<code>
        <Button
            android:id="@+id/btnGame"
            android:layout_width="0dp"
            android:layout_height="wrap_content"
            android:layout_marginEnd="40dp"
            android:layout_marginStart="40dp"
            android:layout_marginTop="16dp"
            android:text="@string/btnGame"
            android:onClick="activityGame"
            app:layout_constraintLeft_toLeftOf="parent"
            app:layout_constraintRight_toRightOf="parent"
            app:layout_constraintTop_toBottomOf="@+id/btnShimmer"
            tools:layout_constraintLeft_creator="1"
            tools:layout_constraintRight_creator="1"/>
</code>
</pre>

6.13 Incluir el llamado al botón MainActivity 
<pre>
<code>
    public void activityGame(View view)
    {
        Intent intent = new Intent(getApplicationContext(), GameActivity.class);
        startActivity(intent);
    }
</code>
</pre>

## Practica 
Implemente una aplicaci�n que haga un insert de un estudiante (id, nombre, edad, telefono) en un DAO utilizando el patr�n MVC. 
Modifique la aplicaci�n para modificar y eliminar los estudiantes utilizando el patr�n MVC. 
