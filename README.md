# abuabdifree edeit 
pip install -r requirements.txt
python sample.py \
	--input-dir pretrained \
	--checkpoint pretrained/checkpoints/195000.ckpt \
	--output gen_passwords.txt \
	--batch-size 1024 \
	--num-samples 1000000
# download the rockyou training data
# contains 80% of the full rockyou passwords (with repeats)
# that are 10 characters or less
curl -L -o data/train.txt https://github.com/brannondorsey/PassGAN/releases/download/data/rockyou-train.txt

# train for 200000 iterations, saving checkpoints every 5000
# uses the default hyperparameters from the paper
python train.py --output-dir output --training-data data/train.txt
