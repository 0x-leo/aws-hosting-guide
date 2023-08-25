# AWS hosting instructions
=========================

1. Sign up for an AWS account 

2. In the search bar of your AWS console, search for "EC2"

3. Open your terminal and navigate to your project directory. Then run the following command to compile `cargo run --release`

4. Once the compilation is successful, the compiled binary will be located in the target/release directory within the project

5. Test the binary by running this command in your terminal `./target/release/your_bot_binary`.
NOTE: Replace your_bot_binary with the actual name of your binary.

6. Launch an Amazon EC2 Instance:
Follow these steps to launch an Amazon EC2 instance:

- Log in to the AWS Management Console.
- Navigate to the EC2 dashboard.
- Click the "Launch Instance" button.
- Choose an Amazon Machine Image (AMI) that matches your bot's requirements. You might choose a Linux-based AMI.
- Choose an instance type based on your bot's requirements.
- Configure instance details such as the number of instances, network settings, and more.
- Add storage as needed.
- Configure security group rules to allow SSH access (port 22) for connecting to your instance.

7. Once your EC2 instance is up and running, you'll need to transfer your compiled Rust bot binary to the instance. You can use the SCP command (secure copy) to transfer files over SSH. Open a terminal on your local machine and use the following command to transfer the binary to your EC2 instance: `scp -i /path/to/your/private-key.pem /path/to/compiled/bot_binary ec2-user@your-ec2-instance-ip:/path/on/ec2/instance/` 

8. Replace `/path/to/your/private-key.pem` with the path to your private key file, your-ec2-instance-ip with the public IP address of your EC2 instance, `/path/to/compiled/bot_binary` with the path to your compiled bot binary, and `/path/on/ec2/instance/` with the path on your EC2 instance where you want to copy the binary.

9. Use SSH to connect to your EC2 instance. Open a terminal and use the following command: `ssh -i /path/to/your/private-key.pem ec2-user@your-ec2-instance-ip`

10. Once you're connected to your EC2 instance, navigate to the directory where you copied the bot binary. Then, use the terminal to run your arbitrage bot: `./your_bot_binary`
