=FindOrb build system=

Initial build script provided by M. Alexandersen:

Hi Brett;

Thanks to one of my colleagues here at the MPC, I now have an eternal bash history (no limit to last 2000 commands or such junk), so I can go back and see exactly what I did in order to install find_orb:
```bash
apt-get install ncurses-dev ncursesw-dev libcurl4-dev libcurl4-nss-dev libcurl4-openssl-dev libncurses5-dev libncursesw5-dev  # You may have some of all these already; on one PC I only had to install the last two, on another I needed all of these. 
mkdir ~/find_orb_setup
cd ~/find_orb_setup
git clone https://github.com/Bill-Gray/lunar.git
git clone https://github.com/Bill-Gray/sat_code.git
git clone https://github.com/Bill-Gray/jpl_eph.git
git clone https://github.com/Bill-Gray/find_orb.git
git clone https://github.com/Bill-Gray/miscell.git
cd lunar/
make
make install
cd ../jpl_eph/
make
make install
cd ../lunar/
make integrat
make install
cd ../sat_code/
make
make install
cd ../find_orb/
make
make install
cd ~/.find_orb
wget ftp://ssd.jpl.nasa.gov/pub/eph/planets/Linux/de430t/linux_p1550p2650.430t
```

And then you _should_ be good to go, find `find_orb` and `fo` being located in your ~/bin/ directory. 
