package com.example.applockerbyface;

import android.content.Intent;
import android.content.SharedPreferences;
import android.content.SharedPreferences.OnSharedPreferenceChangeListener;
import android.os.Bundle;
import android.preference.Preference;
import android.preference.PreferenceActivity;
import android.preference.PreferenceManager;
import android.util.Log;

public class AppLockerPreferenceActivity extends PreferenceActivity {
	@Override
	public void onCreate(Bundle savedInstanceState) {
	    super.onCreate(savedInstanceState);
	    this.addPreferencesFromResource(R.xml.preferences);
	    //the tutorial of PreferenceActivity edit to PreferenceFragment
	    //http://goo.gl/NxJb6D
	    //http://goo.gl/vmAE8I
	    //http://blog.csdn.net/ichliebephone/article/details/5916320
	    PreferenceManager.getDefaultSharedPreferences(this).registerOnSharedPreferenceChangeListener(serviceEnabledListener);
	
	
	    Preference button = (Preference)findPreference("training_user");
	    button.setOnPreferenceClickListener(new Preference.OnPreferenceClickListener() {
	                    @Override
	                    public boolean onPreferenceClick(Preference arg0) { 
	                       Log.e("button", "button");  
	                        return true;
	                    }
	                });
	
	}
	
	OnSharedPreferenceChangeListener serviceEnabledListener = new OnSharedPreferenceChangeListener(){
		public void onSharedPreferenceChanged(
				SharedPreferences sharedPreferences, String key) {
			if (key.equals("service_enabled")){
				if (sharedPreferences.getBoolean(key, false))
					startService();
				else
					stopService();
			}
		}
	};

	private void stopService() {
		this.stopService(new Intent(this, DetectorService.class));
	}

	private void startService() {
		Intent startService = new Intent(this, DetectorService.class);
		this.startService(startService);
	}
}