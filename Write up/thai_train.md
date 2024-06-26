# Command Line: 


# telnet command : là công cụ dòng lệnh dùng để kiểm tra và xử lý các kết nối mạng.
Sử dụng để kiểm tra và kết nối đến các dịch vụ mạng TCP đơn giản như HTTP, SMTP, FTP, v.v.
```
 Telnet [hostname or IP] [port] 
```
![image](https://github.com/eggsy3011/ZenCloud-Train-1/assets/108015833/f451e3cc-47f5-46a6-8866-7c5bca4cda6b)

# nc command: Kết nối từ xa, kiểm tra dịch vụ, chuyển tiếp cổng, quét cổng, truyền tệp
```
nc [options] [hostname or IP] [port]
```
telnet đến port 22 của ip vps lab trả lời port có mở hay không

![image](https://github.com/eggsy3011/ZenCloud-Train-1/assets/108015833/90aef39c-28cd-4d64-884a-b6aa3a550f46)


telnet đến port 20 của ip vps lab trả lời port có mở hay không

![image](https://github.com/eggsy3011/ZenCloud-Train-1/assets/108015833/d4c157c1-5a04-41cd-9489-6970c3b64f64)


ping/hping3 ping đến domain zonecloud.vn sau đó giải thích
```
Ping zonecloud.vn
```
![image-3](https://github.com/eggsy3011/ZenCloud-Train-1/assets/108015833/394dac6c-a6d7-4de2-b71e-03519ce77971)


Kích thước gói tin: 64 bytes. Đây là kích thước của gói tin ICMP 

Địa chỉ IP và hostname của máy chủ phản hồi: 103.130.216.89 (static-89-216-130-103.tino.vn).

Số thứ tự gói tin: 1.

TTL của gói tin phản hồi: 56.

Thời gian hồi đáp từ máy chủ : 5.85 ms.
hping3 :   
```
 hping3 -S zonecloud.vn -p 80
```
-S: Gửi gói SYN (SYN flag set).

zonecloud.vn: Tên miền hoặc địa chỉ IP của mục tiêu.

-p 80: Cổng đích là 80 (HTTP).

![image-4](https://github.com/eggsy3011/ZenCloud-Train-1/assets/108015833/22912c62-fbbb-488f-a5fc-9d1ce2157aa9)


len=44: Chiều dài của gói tin là 44 bytes.

ip=103.130.216.89: Địa chỉ IP của máy chủ phản hồi.

ttl=52: Time to Live của gói tin phản hồi.

sport=0: Cổng nguồn là 0 (do cổng đích mặc định là 0).

flags=RA: Các cờ trong gói tin phản hồi là RST-ACK (Reset and Acknowledge). 
win=0: Kích thước cửa sổ TCP là 0.

rtt=49.9 ms, 50.1 ms, 50.2 ms: Round-trip time - thời gian hồi đáp của các gói tin.


# Ttl= là gì?

Time to Live (TTL) là giá trị cho biết số lượng bước nhảy (hops) mà gói tin có thể đi qua trước khi bị loại bỏ. Mỗi khi gói tin đi qua một router, giá trị TTL sẽ giảm đi một đơn vị. Nếu TTL giảm về 0, gói tin sẽ bị loại bỏ. 

# Time= là gì? 

Đây là thời gian hồi đáp (round-trip time) của gói tin, tính bằng milliseconds (ms). Thời gian này đo lường khoảng thời gian từ khi gói tin được gửi đi cho đến khi nhận được phản hồi từ máy chủ. 


# Ssh command


Dùng password: Khóa SSH cung cấp một cách an toàn hơn để kết nối với máy chủ so với mật khẩu. Để sử dụng khóa SSH, trước tiên bạn cần tạo một cặp khóa SSH và thêm khóa công khai vào máy chủ từ xa.
```
ssh username@remote_host
```
Dùng key: 

# Chúng ta vô vi /etc/ssh/sshd_config
để coi ssh key có cho xác thực hay không với xem đường dẫn đang ở đâu : 

![image](https://github.com/eggsy3011/ZenCloud-Train-1/assets/108015833/724dad6e-5c30-4a47-bedd-0fe37d6a876d)
```
PubkeyAuthentication yes
```
```
 AuthorizedKeysFile      .ssh/authorized_keys
```
# Tạo 1 file tên là keys để lưu key: 

![image](https://github.com/eggsy3011/ZenCloud-Train-1/assets/108015833/a740deb5-3545-49aa-a577-dac79a0d06bb)
# Sau đó ta tạo key: 
```
ssh-keygen  -t rsa 
```
![image](https://github.com/eggsy3011/ZenCloud-Train-1/assets/108015833/757499b9-ac61-4ef8-8c02-19f21c5455c5)

# Lưu tại đường dẫn id_rsa:

![image](https://github.com/eggsy3011/ZenCloud-Train-1/assets/108015833/d023e3cc-a1d7-4616-9279-5e31a1bc36ec)

![image](https://github.com/eggsy3011/ZenCloud-Train-1/assets/108015833/1e187561-846f-407b-a3cd-7fa769d83f24)

![image](https://github.com/eggsy3011/ZenCloud-Train-1/assets/108015833/d2c08118-9d96-466c-90a7-1beaecb9aee6)

# rồi ta phân quyền cho:
chmod 600 /root/.ssh/authorized_keys 

chmod 700 /root/.ssh/

chmod 700 /root
```
 Chmod 600: Chủ sở hữu có quyền đọc và viết, không ai khác có quyền gì.
```
```
Chmod 700: Chủ sở hữu có quyền đọc, viết và thực thi, không ai khác có quyền gì.
```
# Sau đó ta tải keys về máy mình bằng scp 
![image](https://github.com/eggsy3011/ZenCloud-Train-1/assets/108015833/e5a0f1e9-9394-4159-926d-d5ff4821f165)

# Tạo file ssh config và chỉnh sửa bằng vs code :
![image](https://github.com/eggsy3011/ZenCloud-Train-1/assets/108015833/577b8623-16f9-44d8-93ea-6b169843651d)

![image](https://github.com/eggsy3011/ZenCloud-Train-1/assets/108015833/5399bfdc-e06e-4da7-b9df-d64b7c609f4a)

# Ta dùng  ssh -v  -p 1922 root@103.162.20.237  để kiểm tra coi private key có hoạt động hay không?
```
ssh -v  -p 1922 root@103.162.20.237 
```
![image](https://github.com/eggsy3011/ZenCloud-Train-1/assets/108015833/127ae688-c228-4146-9362-d3d7619acfde)

![image](https://github.com/eggsy3011/ZenCloud-Train-1/assets/108015833/2fa1a404-81f7-4153-bb19-a670eaa553fb)

Dùng port custom
```
ssh -p port_number username@remote_host
```
![image](https://github.com/eggsy3011/ZenCloud-Train-1/assets/108015833/0bc6529b-756e-4c2e-b5d2-db425d21a809)

```
ssh -i /path/to/private_key -p port_number username@remote_host
```

scp command : Lệnh scp (Secure Copy) được sử dụng để sao chép các tệp tin và thư mục giữa các máy tính từ xa một cách an toàn qua mạng. Dưới đây là cách sử dụng scp để sao chép một tệp tin và một thư mục.


scp 1 file : 

Từ máy - máy từ xa :
```
scp /path/to/local/file username@remote_host:/path/to/remote/destination
```
Từ máy từ xa - máy  :
```
scp username@remote_host:/path/to/remote/file /path/to/local/destination
```
scp 1 folder: 

Từ máy - máy từ xa : 
```
scp -r /path/to/local/folder username@remote_host:/path/to/remote/destination
```

Từ máy từ xa - máy : 
```
scp -r username@remote_host:/path/to/remote/folder /path/to/local/destination
```
 Nếu là port khác : 
 ```
scp -P port_number /path/to/local/file username@remote_host:/path/to/remote/destination
```
```
 scp -P 19622 /home/nthai/Desktop/file_backup.txt.zip root@103.162.20.237:/root/mtp
```

![image](https://github.com/eggsy3011/ZenCloud-Train-1/assets/108015833/bcc6fae7-d69b-462e-a6d4-ca1f8d9c4cd5)

![image](https://github.com/eggsy3011/ZenCloud-Train-1/assets/108015833/56b03249-89fb-4fbe-8447-2b79a2b70848)

máy từ xa về máy : 




# rsync command : 
Lệnh rsync được sử dụng để đồng bộ hóa và sao chép tệp tin và thư mục giữa các máy tính từ xa hoặc trong cùng một hệ thống. rsync có khả năng đồng bộ hóa chỉ những phần thay đổi, giúp tiết kiệm băng thông và thời gian. Dưới đây là cách sử dụng rsync để sao chép tệp tin, thư mục, và thực hiện đồng bộ hóa gia tăng (incremental synchronization).

 # rsync file : 
Từ máy - máy từ xa: 
```
rsync -avz /path/to/local/file username@remote_host:/path/to/remote/destination
```
Từ máy từ xa - máy:
```
rsync -avz username@remote_host:/path/to/remote/file /path/to/local/destination
```

# rsync folder : 
Từ máy - máy từ xa:
```
rsync -avz /path/to/local/folder username@remote_host:/path/to/remote/destination
```

Từ máy từ xa - máy:
```
rsync -avz username@remote_host:/path/to/remote/folder /path/to/local/destination
```

rsync increamental : tự động thực hiện đồng bộ hóa gia tăng, nghĩa là nó chỉ sao chép các tệp tin đã thay đổi hoặc mới. Cú pháp sử dụng vẫn như các ví dụ trên. 

Các tùy chọn thường dùng:

    -a : Archive mode, đồng bộ hóa toàn bộ thư mục và giữ nguyên thuộc tính của tệp tin.
    -v : Verbose, hiển thị thông tin chi tiết quá trình sao chép.
    -z : Compress, nén dữ liệu trong quá trình truyền để tiết kiệm băng thông.
    --delete : Xóa các tệp tin ở đích mà không còn tồn tại ở nguồn, giúp đồng bộ hóa hoàn toàn.
```
rsync -avz --delete /path/to/local/folder username@remote_host:/path/to/remote/destination
```
```
rsync -avz -e "ssh -p port_number" /path/to/local/file_or_folder username@remote_host:/path/to/remote/destination
```
```
rsync -avz -e " ssh -p 19622" /home/nthai/Desktop/hi\ lại\ là.txt root@103.162.20.237:/root/mtp
```
![image](https://github.com/eggsy3011/ZenCloud-Train-1/assets/108015833/1225bc1d-888d-4d61-b173-562fe6d185a9)

# cat command: Lệnh cat (concatenate) trong Linux được sử dụng để hiển thị nội dung của tệp tin, kết hợp nhiều tệp tin và chuyển nội dung vào tệp tin khác.

# cat nội dung 1 file 
```
cat /path/to/file
```
![image](https://github.com/eggsy3011/ZenCloud-Train-1/assets/108015833/7aeb9eb8-26d0-4908-bd12-e360bcd6b960)


# cat dòng thứ <n> trong file
Đây là nội dung file Test 

![image](https://github.com/eggsy3011/ZenCloud-Train-1/assets/108015833/0a9e7c1a-fb0a-4d74-bfe5-de310b9df9b8)

```
cat -n -E file.txt 
```
![image](https://github.com/eggsy3011/ZenCloud-Train-1/assets/108015833/3c05b6df-d688-4fc4-9040-c0a8ef92d513)

-n: hiện số dòng ở đầu mỗi dòng.

-E: hiện $ để biết điểm cuối dòng.
# cat nhiều dòng vào 1 file bằng EOF:

EOF là ký tự được khai báo và dùng để kết thúc việc nhập liệu, có thể sử dụng một chuỗi bất kỳ thay thế.

$ cat > simple.txt << "EOF"
![image-5](https://github.com/eggsy3011/ZenCloud-Train-1/assets/108015833/0a580262-a342-475e-aad5-9d18bb3e8269)

# echo command:
```
echo "Đây là một dòng mới" >> myfile.txt
```
Dùng echo để chèn thêm 1 dòng vào cuối file.

![image-6](https://github.com/eggsy3011/ZenCloud-Train-1/assets/108015833/221746c8-e7a9-4023-8538-69a77c9e7212)

# Dùng echo để overwirte nội dung của file
```
echo "Đây là một dòng mới" > myfile.txt
```
![image-7](https://github.com/eggsy3011/ZenCloud-Train-1/assets/108015833/bb7ba3f5-c746-46e9-a5e8-60c794906a5e)

tail/head command

Lệnh head được sử dụng để xem những dòng đầu tiên của một file.

 ![image-8](https://github.com/eggsy3011/ZenCloud-Train-1/assets/108015833/a79f117d-81ed-493c-ba5f-d444c3e62f3c)


# Head 5 dòng đầu tiên: 
```
head -n 5 myfile.txt
```
![image-9](https://github.com/eggsy3011/ZenCloud-Train-1/assets/108015833/78b6f915-00f0-4226-bb7f-e687708ca2a2)


# Tail và tailf
Lệnh tail được sử dụng để xem những dòng cuối cùng của một file.
```
tail [tùy chọn] <tên_file>
```
![image-10](https://github.com/eggsy3011/ZenCloud-Train-1/assets/108015833/a6a58122-81b5-44e2-aae5-485c679b82fa)


# Hiển thị 5 dòng cuối cùng của file 

tail -n 5 myfile.txt

![image-11](https://github.com/eggsy3011/ZenCloud-Train-1/assets/108015833/938df0c6-ae7c-44fc-a5c3-c34f496f064e)

# Lệnh tailf được sử dụng để theo dõi nội dung cuối cùng của file và cập nhật liên tục khi có sự thay đổi. Nó tương tự như tail -f nhưng được tối ưu hóa cho việc theo dõi log files.
```
tailf <tên_file>
```
```
tailf /var/log/syslog
```
![image-12](https://github.com/eggsy3011/ZenCloud-Train-1/assets/108015833/2224ad59-4907-433d-882e-05960f882ae7)

```
tail -n 20 -f /var/log/syslog
```
![image-13](https://github.com/eggsy3011/ZenCloud-Train-1/assets/108015833/bec52a12-045c-4dd7-990c-2ef5cd07d747)

# Sed command : Lệnh sed (stream editor) trong Unix/Linux là một công cụ mạnh mẽ để tìm kiếm và thay thế chuỗi trong file.

Dùng Sed để find and replace một string trong file
```
sed 's/find_string/replace_string/g' filename
```
![image-14](https://github.com/eggsy3011/ZenCloud-Train-1/assets/108015833/085874b2-2930-4a9c-9cde-ca3c7270ca5e)


's': Bắt đầu một lệnh thay thế.
'find_string': Chuỗi bạn muốn tìm kiếm.
'replace_string': Chuỗi bạn muốn thay thế.
'g': Toán tử toàn cục (global), để thay thế tất cả các trường hợp xuất hiện của find_string trong mỗi dòng. Nếu không có g, chỉ lần xuất hiện đầu tiên trong mỗi dòng sẽ được thay thế.
filename: Tên file nơi bạn muốn thực hiện thay thế.

Ví dụ: file hi có nội dung new word ta thay thế bằng old word 

![image-15](https://github.com/eggsy3011/ZenCloud-Train-1/assets/108015833/a21462ca-b3cd-4bf1-be54-b90ba42347c2)


# traceroute/tracert command

# Lệnh traceroute (hoặc tracert trên Windows) được sử dụng để theo dõi đường đi của các gói tin từ máy tính của bạn đến một máy chủ đích. Nó liệt kê tất cả các thiết bị mạng (routers) mà gói tin đi qua trên đường đến đích. Đây là một công cụ hữu ích để chẩn đoán các vấn đề kết nối mạng.

# Traceroute google.com (địa chỉ biến) 

![image-16](https://github.com/eggsy3011/ZenCloud-Train-1/assets/108015833/058cf6d0-8ca4-4baa-afba-b75f445d4225)

![image-17](https://github.com/eggsy3011/ZenCloud-Train-1/assets/108015833/a1f679d0-8ef3-45ea-8cdc-9d71523569bc)


1. Sử dụng mạng Gpon.net 
2.localhost gói tin chạy dao động 9-10-11s chạy ổn định
3.điểm đến cuối là static-89-216-130-103.tino.vn 

Sau khi traceroute xong giải thích chi tiết kết quả trả về

# Netstat command : sử dụng netstat, người dùng có thể theo dõi và kiểm tra các kết nối mạng đang hoạt động trên hệ thống của họ, giúp họ xác định và giải quyết các vấn đề liên quan đến mạng hoặc bảo mật. 

Hiển thị tất cả các socket TCP đang listen:
```
netstat -tlnp
```
![image-19](https://github.com/eggsy3011/ZenCloud-Train-1/assets/108015833/910abae2-ce7b-475b-8f31-a50f4b52ce2e)

'-t': Chỉ hiển thị thông tin về các socket TCP.

'-l': Chỉ hiển thị các socket đang listen.

'-n': Không giải quyết tên máy chủ hoặc tên cổng.

'-p': Hiển thị tên chương trình và PID của tiến trình đang sử dụng socket.
```
netstat -ulnp
```

![image-18](https://github.com/eggsy3011/ZenCloud-Train-1/assets/108015833/455b11cc-5ae7-4946-9028-c6b5b2423974)


'-u': Chỉ hiển thị thông tin về các socket UDP.

'-l': Chỉ hiển thị các socket đang listen.

'-n': Không giải quyết tên máy chủ hoặc tên cổng.

'-p': Hiển thị tên chương trình và PID của tiến trình đang sử dụng socket.

# Don't resolve hostname
```
netstat -nl
``` 
![image-20](https://github.com/eggsy3011/ZenCloud-Train-1/assets/108015833/600278dc-790a-422c-b945-4a0dbd807b11)

# Don't resolve portname
```
netstat -nl
```
# Display process name/PID
```
netstat -nlp
```
![image-21](https://github.com/eggsy3011/ZenCloud-Train-1/assets/108015833/7fb8902c-46f3-44b8-b299-37aea96cb0e2)



# Only show tcp socket 
```
netstat -nlt
```
![image-22](https://github.com/eggsy3011/ZenCloud-Train-1/assets/108015833/fd658174-b698-4ead-9ed4-347eb179a586)


# Only show udp socket
```
netstat -nlu
```
![image-23](https://github.com/eggsy3011/ZenCloud-Train-1/assets/108015833/402c4355-1149-4d55-89f8-eb30fccc21bc)


# Sort command : giúp người dùng sắp xếp lại văn bản theo 1 thứ tự nhất định. 

sort theo thứ tự tăng dần 
sort file.txt
![image-24](https://github.com/eggsy3011/ZenCloud-Train-1/assets/108015833/181db60c-14f1-451c-9ae7-d825dd42f12c)


# Sort theo thứ tự giảm dần
```
sort -r file.txt
``` 
![image-25](https://github.com/eggsy3011/ZenCloud-Train-1/assets/108015833/f26f70ea-488c-400c-ba5b-744247ba566d)


# Sort theo column
```
sort -k numbercolum  file.txt
```
ví dụ ta có file: 

![image](https://github.com/eggsy3011/ZenCloud-Train-1/assets/108015833/6d41c066-1714-4405-81b1-206a48a774fa)

sort -k 2 filetest.txt
sort -k 3 filetest.txt

 ![image](https://github.com/eggsy3011/ZenCloud-Train-1/assets/108015833/f8534b73-9495-4ff7-9d9f-a9f545da5cc7)


# Uniq command
# Lệnh uniq trong Linux được sử dụng để hiển thị các dòng giống hệt nhau trong tệp văn bản. Lệnh này có thể hữu ích nếu bạn muốn xóa các từ hoặc chuỗi trùng lặp khỏi tệp văn bản. Vì lệnh uniq so sánh các dòng liền kề để tìm các bản sao thừa, nó chỉ hoạt động với các tệp văn bản đã được sắp xếp.

Để ví dụ về Uniq thì ta tạo 1 tệp tin robo.txt có dạng như sau: 

![image](https://github.com/eggsy3011/ZenCloud-Train-1/assets/108015833/64b2e151-9d94-4e82-a05b-3aa1df34de71)

Ví dụ 1: Loại bỏ các dòng trùng lặp:

Lệnh cơ bản uniq sẽ loại bỏ các dòng trùng lặp :
```
uniq robo.txt 
```
![image](https://github.com/eggsy3011/ZenCloud-Train-1/assets/108015833/36c968f1-7d9b-48f8-8295-09cdcbe5b071)

Ví dụ 2: Đếm số lần xuất hiện của các dòng

Sử dụng tùy chọn -c để đếm số lần xuất hiện của mỗi dòng:

```
uniq -c robo.txt
```
![image](https://github.com/eggsy3011/ZenCloud-Train-1/assets/108015833/92c6447d-70c9-47c1-bf3c-48588892b3e9)

Ví dụ 3: Chỉ hiển thị các dòng bị trùng lặp

Sử dụng tùy chọn -d để chỉ hiển thị các dòng bị trùng lặp:

```
uniq -d robo.txt 

```
![image](https://github.com/eggsy3011/ZenCloud-Train-1/assets/108015833/e4be44cb-1d71-4390-bde6-6c759526778e)

Ví dụ 4: Chỉ hiển thị các dòng không bị trùng lặp

Sử dụng tùy chọn -u để chỉ hiển thị các dòng không bị trùng lặp:

```
uniq -u  robo.txt 
```
![image](https://github.com/eggsy3011/ZenCloud-Train-1/assets/108015833/f4a4c258-2363-4e59-82ec-db8336eb99cd)

Ví dụ 5: Sắp xếp và loại bỏ các dòng trùng lặp

Để đảm bảo tất cả các dòng trùng lặp được loại bỏ, bạn cần sắp xếp tập tin trước khi dùng uniq:
```
sort robo.txt | uniq
```
![image](https://github.com/eggsy3011/ZenCloud-Train-1/assets/108015833/98f82b85-81fe-4e34-8274-209a115e44b4)

Ví dụ 6: Đếm số lần xuất hiện của các dòng sau khi sắp xếp

Kết hợp sort và uniq -c để đếm số lần xuất hiện sau khi sắp xếp:

```
sort robo.txt | uniq -c
```
![image](https://github.com/eggsy3011/ZenCloud-Train-1/assets/108015833/423ea0d7-cf77-478b-a46a-b866601e69cd)



# Wc command : lệnh wc cho phép bạn đếm số dòng, từ, ký tự và byte của mỗi tệp nhất định hoặc đầu vào tiêu chuẩn và in kết quả.

# Đếm số dòng trong file: 
```
wc -l tên_tệp_tin
```
![image-29](https://github.com/eggsy3011/ZenCloud-Train-1/assets/108015833/9ac43e2d-3513-4198-bbe0-bddf532c6251)

# Đếm số kí tự trong file:
```
wc -m tên_tệp_tin 
```
![image-30](https://github.com/eggsy3011/ZenCloud-Train-1/assets/108015833/be518301-06ab-47ed-85b0-e5236f89f1e1)


# Chmod, chown, chattr command
# Phân quyền trong Linux là một khía cạnh rất quan trọng giúp quản lý quyền truy cập vào các tệp và thư mục trong hệ thống file của bạn

Ở đây ta thấy file test có rw--r--r không có quyền execute.

![image](https://github.com/eggsy3011/ZenCloud-Train-1/assets/108015833/1c2e8355-8f49-4e56-be6a-78ae21e7866b)

Ta dùng chmod -R 777 <tên_thư_mục> để đầy đủ phân quyền.

![image](https://github.com/eggsy3011/ZenCloud-Train-1/assets/108015833/19b502f8-c854-4681-ac0a-ef72172c94be)


# Quyền Truy Cập Cơ Bản:

    Read (R): Cho phép đọc nội dung của tệp hoặc thư mục.
    Write (W): Cho phép sửa đổi nội dung của tệp hoặc thư mục.
    Execute (X): Cho phép thực thi tệp hoặc truy cập thư mục.

# Quyền Áp Dụng Cho Người Dùng:

    Chủ Sở Hữu (Owner): Người tạo ra tệp hoặc thư mục, có thể quyết định quyền truy cập.
    Nhóm (Group): Các người dùng thuộc vào một nhóm có thể có các quyền riêng biệt.
    Khác (Others): Tất cả những người dùng khác ngoài chủ sở hữu và nhóm.
Trong đó:

    u là chủ sở hữu (user), g là nhóm (group), o là những người dùng khác (others), a là tất cả (all).
    + thêm quyền, - gỡ bỏ quyền, = gán quyền.
   
```
    chmod u+x example.txt
```
# Thay đổi chủ sở hữu và nhóm với chown

Để thay đổi chủ sở hữu và nhóm của một tệp tin hoặc thư mục:
          chown user:group tên_tệp_tin_đích

đầu tiên ta tạo useradd và group add
![image](https://github.com/eggsy3011/ZenCloud-Train-1/assets/108015833/4bee65ea-8756-484e-9176-4d2bdd745c03)

và thay đổi chủ sỡ hữu và nhóm user1 và group1:

![image](https://github.com/eggsy3011/ZenCloud-Train-1/assets/108015833/83a81736-e890-4a58-a173-5815862c7423) 

Lệnh chattr +i là để đặt thuộc tính "immutable" (không thể thay đổi) cho một tệp tin hoặc thư mục trong hệ thống Linux. Khi một tệp tin hoặc thư mục có thuộc tính này, nó không thể bị xóa, sửa đổi, đổi tên, hoặc di chuyển mà không được gỡ bỏ trước.
    chattr +i tên_tệp_tin_đích

    



# find command: 

Lệnh find là một công cụ tìm kiếm tệp tin trong hệ thống Linux.

Cho phép người dùng tìm kiếm theo nhiều tiêu chí như tên file, kích thước file, thời gian tạo hoặc sửa đổi file, quyền truy cập file, v.v.

Lệnh find trong linux thường được sử dụng để tìm kiếm các tệp tin trong các thư mục lớn, hoặc để tìm kiếm các tệp tin theo các tiêu chí cụ thể.
Ta tạo 3 file để test.

![image](https://github.com/eggsy3011/ZenCloud-Train-1/assets/108015833/e0f7bd31-ef74-498d-9d34-bde7f48aa781)


```
find . -type f -name "abc1.txt"

```
![image](https://github.com/eggsy3011/ZenCloud-Train-1/assets/108015833/9645a947-01eb-40be-87f1-639765de3fba)

```
find các folder có tên abc
```
```
find . -type d -name "abc"
```
ví dụ ở đây ta đang có folder abc 

![image](https://github.com/eggsy3011/ZenCloud-Train-1/assets/108015833/d5f01a29-89cb-4779-8d6a-742cc116fd1a)

thì khi ta ở /home muốn tìm folder abc ta dùng: 

find . -type d -name "abc"

![image](https://github.com/eggsy3011/ZenCloud-Train-1/assets/108015833/269e689b-e80d-438f-9d93-c6656da90d05)



```
find các file có đuôi .log
```
```
find . -type f -name "*.log"
```
![image](https://github.com/eggsy3011/ZenCloud-Train-1/assets/108015833/3429640c-1087-4d34-b4f8-98ff16d27511)



```
find các file có tên abc và thực hiện phần quyền read only cho file
```
```
find . -type f -name "abc" -exec chmod 400 {} \;
```
![image](https://github.com/eggsy3011/ZenCloud-Train-1/assets/108015833/9e28ce34-bdcc-4d3a-b2c6-3d755ff7da3d)

khi phân quyền chmod 400 xong ta vào ktra: 

![image](https://github.com/eggsy3011/ZenCloud-Train-1/assets/108015833/81484a01-d604-4cf7-b3cb-52bd0c73540b)




