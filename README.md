# Turtlebot4 — Pick & Place Item with Buzzer Indicator  
Mid-Semester Exam – RE702 Localization and Mapping  
Case Study: Autonomous Delivery Robot (From Room 203 → Lobby BRAIL)

Robot Turtlebot4 melakukan misi otomatis untuk mengambil barang dari Room 203 dan mengantarkannya ke Lobby BRAIL menggunakan ROS2 Navigation (Nav2), SLAM Toolbox (Mapping), AMCL (Localization), Autonomous Navigation, dan Buzzer sebagai indikator. Buzzer berbunyi 1 kali saat robot tiba di titik PICK dan berbunyi 2 kali saat robot tiba di titik PLACE.

1. Koneksi ke Turtlebot4  
Pastikan laptop terhubung ke Turtlebot4 melalui kabel LAN.  
SSH ke robot:  
ssh ubuntu@192.168.185.3

2. Build Workspace dan Install Dependencies  
Buat workspace:  
mkdir -p kelompok1/src  
cd kelompok1  
Clone repository:  
git clone https://github.com/annisashinta29/Turtlebot4-Pick-and-Place-the-Item-and-Activate-Buzzer-as-Indicator.git  
Install dependencies:  
cd ../  
rosdep install --from-paths src --ignore-src -r -y  
Build workspace:  
colcon build

3. Mapping (SLAM) — Jika sudah punya map, lewati langkah ini  
Jalankan SLAM:  
ros2 launch turtlebot4_navigation slam.launch.py  
Buka RViz:  
ros2 launch turtlebot4_viz view_navigation.launch.py  
Gerakkan robot untuk membentuk map:  
ros2 run teleop_twist_keyboard teleop_twist_keyboard --ros-args -p stamped:=true  
Simpan map:  
ros2 service call /slam_toolbox/save_map slam_toolbox/srv/SaveMap "name:  
  data: 'map_name'"  
Map akan menghasilkan file map_name.yaml dan map_name.pgm.

4. Load Map dan AMCL (Localization)  
Setelah map dibuat, jalankan localization:  
ros2 launch turtlebot4_navigation localization.launch.py map:=Mapping_Kelompok1APagiUTS.yaml params:=localization.yaml  
Tahap ini memuat map, mengaktifkan AMCL, dan menentukan posisi robot di map.

5. Jalankan Navigation2 (Nav2)  
Setelah AMCL aktif, jalankan Nav2:  
ros2 launch turtlebot4_pick_place uts_nav.launch.py  
Tunggu sampai muncul pesan "Nav2 is active". Robot siap menerima waypoint.

6. Buka RViz untuk Navigasi  
ros2 launch turtlebot4_viz view_navigation.launch.py  
RViz menampilkan map, posisi robot, path planning, dan pergerakan realtime.

7. Jalankan Program Pick & Place  
Masuk workspace dan source environment:  
cd kelompok1  
source install/setup.bash  
Jalankan misi:  
ros2 run uts uts  
Program akan menavigasi robot ke Room 203 (buzzer bunyi 1x), lalu ke Lobby BRAIL (buzzer bunyi 2x).

Notes:  
- Pastikan posisi awal robot sama seperti posisi pada map.  
- Jangan terlalu cepat berpindah waypoint, gunakan time.sleep().  
- Jika map berbeda, waypoint harus disesuaikan.  
- Nav2 harus ACTIVE sebelum menjalankan program.

Video Demonstration:  
Demo Pick & Place: https://youtu.be/1zIipldbOK8  
Generate Map & Navigasi: https://youtu.be/IZZtBOe8N9M
