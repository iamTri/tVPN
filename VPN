package com.tri.vpn;

import org.bukkit.plugin.java.*;
import org.bukkit.*;
import org.bukkit.command.ConsoleCommandSender;
import org.bukkit.plugin.*;
import org.bukkit.event.player.*;
import java.util.*;
import java.net.*;
import java.io.*;
import org.bukkit.event.*;

public class VPN extends JavaPlugin implements Listener
{
    public void onEnable() {
        Bukkit.getPluginManager().registerEvents((Listener)this, (Plugin)this);
        this.getConsoleCommandSender().sendMessage(ChatColor.translateAlternateColorCodes('&', "&8&m-----------------------------------------------------"));
        this.getConsoleCommandSender().sendMessage(ChatColor.translateAlternateColorCodes('&', "                  &6tVPN &8&m-&e By imTri"));
        this.getConsoleCommandSender().sendMessage(ChatColor.translateAlternateColorCodes('&', ""));
        this.getConsoleCommandSender().sendMessage(ChatColor.translateAlternateColorCodes('&', "               &9Your server is now safe from VPN users                "));
        this.getConsoleCommandSender().sendMessage(ChatColor.translateAlternateColorCodes('&', "&8&m-----------------------------------------------------"));
    }
    
    
    @EventHandler(priority = EventPriority.LOWEST)
    public void onLogin(final PlayerLoginEvent event) {
        if (!event.getPlayer().hasPermission("antiproxy.bypass")) {
            try {
                final String url = "http://iphub.info/api.php?ip=&showtype=3" + event.getAddress().getHostAddress() + "&showtype=3";
                final Scanner scanner = new Scanner(new URL(url).openStream());
                if (scanner.findInLine("Proxy: 1") != null) {
                    event.disallow(PlayerLoginEvent.Result.KICK_OTHER, "§cWe do not allow §dVPN usage §con the hCartels Network.\n§7If this is an error, please join §fts.cartels.pw§7.");
                }
                scanner.close();
            }
            catch (MalformedURLException exception) {
                exception.printStackTrace();
            }
            catch (IOException exception2) {
                exception2.printStackTrace();
            }
        }
    }
    public ConsoleCommandSender getConsoleCommandSender() {
        return Bukkit.getServer().getConsoleSender();
    }
    
}
