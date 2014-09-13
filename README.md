package me.twxaoes.Medic;

import org.bukkit.Bukkit;
import org.bukkit.ChatColor;
import org.bukkit.command.Command;
import org.bukkit.command.CommandSender;
import org.bukkit.entity.Player;
import org.bukkit.plugin.java.JavaPlugin;

public class Medic extends JavaPlugin {
	
	public void onEnable() {
		
	}
	
	public void onDisable() {
		Bukkit.getServer().getLogger().info("Medic disabled!");
			
	}

	@SuppressWarnings("deprecation")
	public boolean onCommand(CommandSender sender, Command cmd, String commandLabel, String[] args) {
		
		if (!(sender instanceof Player)) {
			sender.sendMessage(ChatColor.RED + "The console cannot use Medic!");
		}
		
		Player player = (Player) sender;
		
		if (cmd.getName().equalsIgnoreCase("heal")) {
			if (args.length == 0) {
				player.setHealth(20);
				player.sendMessage(ChatColor.GREEN + "You have been healed!");
				return true;
			}
			Player target = Bukkit.getServer().getPlayer(args[0]);
			if (target == null) {
				player.sendMessage(ChatColor.RED + "Could not find player!");
				return true;
			}
			target.setHealth(20);
			target.sendMessage(ChatColor.GREEN + "You have been healed!");
			target.sendMessage(ChatColor.GREEN + target.getName() + "Has been healed!");				
		}
		
		if (cmd.getName().equalsIgnoreCase("feed")) {
			if (args.length == 0) {
				player.setFoodLevel(20);
				player.sendMessage(ChatColor.GREEN + "You have been fed!");
				return true;
			}
			Player target = Bukkit.getServer().getPlayer(args[0]);
			if (target == null) {
				player.sendMessage(ChatColor.RED + "Could not find player!");
				return true;
			}
			target.setFoodLevel(20);
			target.sendMessage(ChatColor.GREEN + "You have been fed!");
			target.sendMessage(ChatColor.GREEN + target.getName() + "Has been fed!");				
		}
		return true;
		
	}

}
	
