
CookieHandler.setDefault(cookieManager);
            HttpLoggingInterceptor interceptor = new HttpLoggingInterceptor();
            interceptor.setLevel(HttpLoggingInterceptor.Level.BODY);
            OkHttpClient client = new OkHttpClient.Builder().addInterceptor(interceptor)
                    .cache(cache)
                    .cookieJar(new JavaNetCookieJar(cookieManager)).build();
            Gson gson = new GsonBuilder()
                    .setLenient().create();
            OkHttpClient.Builder builder = new OkHttpClient.Builder();
            builder.connectTimeout(10, TimeUnit.MINUTES) // connect timeout
                    .writeTimeout(10, TimeUnit.MINUTES) // write timeout
                    .readTimeout(10, TimeUnit.MINUTES);
