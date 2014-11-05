CodePic
=======
final String ApiKey = "AIzaSyD8Gd8b9fdqWJ7EVqzdVvPdvG1qTDKfWu0";
GooglePlaceSearch gp;
gp = new GooglePlaceSearch(ApiKey);
gp.setOnPlaceResponseListener(new OnPlaceResponseListener() {
				public void onResponse(String status, final ArrayList<ContentValues> arr_data,Document doc) {
					 textStatus.setText("Status : "+status);
					
					if(status.equals(GooglePlaceSearch.STATUS_OK)) {
						
				ArrayList<String> array = new ArrayList<String>();
						String[] array_photo = new String[30];
						for(int i = 0 ; i < arr_data.size(); i++) {
							array_photo[i] = arr_data.get(i).getAsString(GooglePlaceSearch.PLACE_PHOTO);
							gp.getPhotoBitmapByWidth(array_photo[i], 150, "", new OnBitmapResponseListener() {
								public void onResponse(Bitmap bm, String tag) {
									imgpic.setImageBitmap(bm);
								}
							});
						}//for
