package me.lolmelon.dropdel;

import org.bukkit.Bukkit;
import org.bukkit.entity.Item;
import org.bukkit.event.EventHandler;
import org.bukkit.event.Listener;
import org.bukkit.event.entity.ItemSpawnEvent;
import org.bukkit.plugin.java.JavaPlugin;

public class DropDel extends JavaPlugin implements Listener {

	
	
    @Override
    public void onEnable() {
    	System.out.println("[DropDel] Plugin sucessfully enabled");
    	this.getServer().getPluginManager().registerEvents(this, this);
    }
    @Override
    public void onDisable() {
    	System.out.println("[DropDel] Plugin sucessfully disabled");
    }
    
	@EventHandler
	public void onItemDrop (final ItemSpawnEvent e) {
		
            Bukkit.getScheduler().scheduleSyncDelayedTask(this, new Runnable() {
            	
            	Item drop = e.getEntity();
            	
				@Override
				public void run() {
		                drop.getItemStack().setAmount(0);
		            
				}
            	
            }, 20*5);
        }
}
