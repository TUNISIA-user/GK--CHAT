# GK--Chat
This app will get facebook and instgram and tiktok and whats app and twitter and snapchat and Bsky die : ) 🔥

# this graph for our project

<img src="graph.png"/>


# WORK 
 <pre>

     const mongoose = require('mongoose');

// User Schema
const userSchema = new mongoose.Schema({
    username: { type: String, required: true },
    email: { type: String, required: true, unique: true },
    passwordHash: { type: String, required: true },
});

const User = mongoose.model('User', userSchema);

// Message Schema
const messageSchema = new mongoose.Schema({
    sender_id: { type: mongoose.Schema.Types.ObjectId, ref: 'User', required: true },
    recipient_id: { type: mongoose.Schema.Types.ObjectId, ref: 'User', required: true },
    content: { type: String, required: true },
    created_at: { type: Date, default: Date.now }
});

const Message = mongoose.model('Message', messageSchema);

// Friendship Schema
const friendshipSchema = new mongoose.Schema({
    user_id1: { type: mongoose.Schema.Types.ObjectId, ref: 'User', required: true },
    user_id2: { type: mongoose.Schema.Types.ObjectId, ref: 'User', required: true },
    created_at: { type: Date, default: Date.now }
});

friendshipSchema.index({ user_id1: 1, user_id2: 1 }, { unique: true }); // Ensure unique friendships

const Friendship = mongoose.model('Friendship', friendshipSchema);

// Notification Schema
const notificationSchema = new mongoose.Schema({
    user_id: { type: mongoose.Schema.Types.ObjectId, ref: 'User', required: true },
    type: { type: String, required: true }, // e.g., 'message', 'friend_request'
    reference_id: { type: mongoose.Schema.Types.ObjectId, required: true }, // e.g., message ID or post ID
    content: { type: String, required: true },
    created_at: { type: Date, default: Date.now }
});

const Notification = mongoose.model('Notification', notificationSchema);

// Session Schema
const sessionSchema = new mongoose.Schema({
    user_id: { type: mongoose.Schema.Types.ObjectId, ref: 'User', required: true },
    token: { type: String, required: true, unique: true },
    created_at: { type: Date, default: Date.now },
    expires_at: { type: Date, required: true }
});

const Session = mongoose.model('Session', sessionSchema);

module.exports = {
    User,
    Message,
    Friendship,
    Notification,
    Session
};


     
 </pre>
